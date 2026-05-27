QA Bug Reports Portfolio 

About
This repository contains comprehensive bug reports created during manual and API testing practice, formatted in a professional Jira-style layout. It demonstrates my ability to identify defects across both frontend (UI) and backend (API) layers.

---

1. Web UI Testing (SauceDemo)
* **Tested Application:** [SauceDemo](https://www.saucedemo.com/) (E-commerce web application)
* **Skills Demonstrated:** Functional testing, UI/UX validation, Boundary Value Analysis, Equivalence Partitioning.

UI Bug Reports
| ID | Title | Severity | Priority | Link |
|:---|:---|:---:|:---:|:---:|
| 1 | Cart badge displays incorrect item count | Medium | High | [View Report](./web-ui/bug-reports/BUG-001_cart_badge.md) |
| 2 | Cart items are removed after navigating back from checkout | High | High | [View Report](./web-ui/bug-reports/BUG-002_cart_items_removal.md) |
| 3 | Total price does not include tax | High | High | [View Report](./web-ui/bug-reports/BUG-003_tax_calculation.md) |

---

2. REST API Testing (Postman)
* **Tested Application:** [Practice Software Testing](https://api.practicesoftwaretesting.com) (Toolshop API)
* **Skills Demonstrated:** API testing, Response Status Code validation, Authentication flow analysis, Postman Collection management.

API Bug Reports
| ID | Title | Severity | Priority | Link |
|:---|:---|:---:|:---:|:---:|
| 1 | Error 401 Unauthorized when retrieving profile data without a token | High | High | [View Report](./postman-api/bug-reports/BUG-001_unauthorized_get_user.md) |

---

## 📂 Project Structure
```text
├── web-ui/                # Web UI testing artifacts (SauceDemo)
│   └── bug-reports/       # Markdown files with UI bug reports
│
└── postman-api/           # REST API testing artifacts (Postman)
    ├── bug-reports/       # Markdown files with API bug reports
    └── collections/       # Exported Postman collection JSON files

Goal
To demonstrate structural, high-quality test-design thinking and clear bug reporting skills required for entry-level QA engineer positions.
