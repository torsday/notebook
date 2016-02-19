# Persistence

---

## Directory vs Database

A **directory** is similar to a database, but
- Tends to **contain more descriptive, attribute-based information**.
- Generally **read from more often than written to**.
- Tuned to give **quick-response to high-volume requests**.
- They may have the **ability to replicate information widely** in order to increase availability and reliability, while reducing response time.
    - Temporary inconsistencies between the replicas may be OK, as long as they get in sync eventually.
