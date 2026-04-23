# SQLite DB vs Shared Preferences

## Use Shared Preferences for:

Small, simple key-value data such as:

* Theme / dark mode
* Feature flags
* First launch completed
* Last sync timestamp
* Selected language
* User settings
* Small primitive user state

**Best when:**

* Few values
* Simple reads/writes
* No querying needed
* UI State

---

## Use SQLite DB for:

Structured, growing, or queryable data such as:

* Lists of records
* Forms / submissions
* Messages / history
* Downloaded content
* Offline business data
* Queues / retries
* Parent-child relationships

**Best when:**

* Many records
* Need search / sort / filter
* Need transactions
* Data evolves over time

---

## Quick Decision Rule

| If data is...           | Use                |
| ----------------------- | ------------------ |
| App settings / flags    | Shared Preferences |
| Single values           | Shared Preferences |
| Records / lists         | SQLite             |
| Searchable / filterable | SQLite             |
| Growing over time       | SQLite             |

---

## Avoid

* Large JSON blobs in Shared Preferences
* Using SQLite for isolated flags or intermediate properties
* Complex structured data in Shared Preferences

---

## Team Principle

**If data is state → Shared Preferences**
**If data is records → SQLite**
