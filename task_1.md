
**1. Introduction**
Brute‑force attacks are a class of password‑guessing assaults in which an adversary systematically attempts large numbers of credential combinations until a valid pair is found. Against RDP (Remote Desktop Protocol), these attacks generate high volumes of failed logins over short periods, creating a distinctive pattern of “no successes” followed by repeated failures. Detecting this pattern quickly is critical to preventing unauthorized access.


**2. Brief Setup Steps**
Before running our detection query, ensure you have:

1. **Hydra** (or any password‑spraying tool) installed on your attacker machine.
2. **Splunk Enterprise** set up to receive Windows Security logs.
3. **Universal Forwarder** installed on the Windows host, with `inputs.conf` enabled for the Security event log and `outputs.conf` pointed at your Splunk indexer.

These components let you simulate RDP brute‑force attempts and ingest the resulting EventCode 4624/4625 records into Splunk for analysis.


**3. Core Logic of the Detection Query**
Our SPL query implements a simple two‑window check over fixed 10‑minute buckets:

* **Bucket and count**: Group all RDP login events into ten‑minute intervals, tallying failures (4625) and successes (4624).
* **Look ahead**: For each bucket, peek at the very next bucket’s success count.
* **Flagging rule**: Mark a bucket as a brute‑force event if it hasn greater than **zero successful logins**, **more than six failures**, **and** the following bucket also has greater than **zero successes**.
* **Filter and display**: Finally, only those buckets meeting the rule are output, showing timestamp, success count, failure count, and a “yes” indicator for brute‑force.

This approach reliably isolates windows where an attacker is clearly hammering password guesses without any legitimate success.

---

**4. Conclusion**
By combining simple time‑based aggregation with a two‑step look‑ahead, this SPL pattern offers an efficient way to spotlight RDP brute‑force attempts in real time. It can be scheduled as a saved search or alert, delivering rapid notification whenever an attacker’s failure spree crosses the defined threshold. As part of a layered defense strategy, this logic helps security teams detect and respond to credential‑guessing campaigns before they succeed.



![image](https://github.com/user-attachments/assets/46e7a3e3-9027-4030-b6ef-7ca1e192b85c)



![image](https://github.com/user-attachments/assets/8b651a2f-20fd-45e8-8682-228020a59ad3)



![image](https://github.com/user-attachments/assets/e014d61b-2c10-491d-bcf6-45d35de8b132)

