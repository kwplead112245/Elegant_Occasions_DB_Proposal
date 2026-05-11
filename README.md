# Elegant_Occasions_DB_Proposal

<div align="center">
  <img src="https://img.shields.io/badge/Database-MySQL%208.4-blue?style=for-the-badge&logo=mysql" alt="MySQL Badge">
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" alt="License Badge">
  <img src="https://img.shields.io/badge/Status-Proposal-green?style=for-the-badge" alt="Status Badge">
</div>

<br />

<div align="center">

### Relational Database Solution for Operational Event Management
<p><i>Standardizing wedding planning logistics for Elegant Occasions, LLC.</i></p>

</div>

---

### Project Overview

This project presents a formal database design developed as part of the DBA 120 curriculum at AB Tech. It transitions Elegant Occasions, LLC from fragmented tracking to a centralized, high-integrity system optimized for 3rd Normal Form (3NF).

> **Important:** This design is operational only. Financial systems (invoicing/billing) are explicitly out of scope to prioritize event logistics and decision tracking.

---

### Key Requirements and Scope

The architecture is strictly governed by the original RFP and interview findings.

#### Design Constraints
* **Multiple Clients per Wedding:** Couples are linked to weddings via a junction table, supporting both partners and any associated coordinators.
* **Service Integrity:** Every appointment requires at least one service and one assigned employee.
* **Venue Logistics:** Enforced guest capacity checks.

#### Design Restraints
* **No Overlaps:** Prevention of conflicting client appointments.
* **Mandatory Staffing:** Appointments cannot exist without an assigned employee.

---

### Stakeholder Research

<details open>
<summary><b>Click to toggle Employee Interview Insights</b></summary>

| Stakeholder | Role | Requirement Integrated |
| :--- | :--- | :--- |
| <div align="center">Ava Reynolds</div> | <div align="center">Operations Manager</div> | Tracking service tier changes & Decision Log for approvals. |
| <div align="center">Sophie Lang</div> | <div align="center">Senior Planner</div> | Vendors remain unlinked until a contract is formally signed. |
| <div align="center">Grant Dwyer</div> | <div align="center">IT Specialist</div> | Status values enforced via MySQL ENUM types for data integrity. |

</details>

---

### Technical Architecture

The system utilizes a series of junction tables to handle complex many-to-many relationships (e.g., `vendor_service`, `wedding_service`, `client_wedding`).

* **RDBMS:** MySQL 8.4 (LTS)
* **Core Entities:** Clients, Weddings, Employees, Services, Vendors, Venues.
* **Status Management:** Service, contract, and appointment statuses enforced as MySQL ENUMs directly on their respective columns.
* **Audit Trail:** Implementation of a `decision_log` to answer "who agreed to what and when."

---

### Permission Model

<table>
  <tr style="background-color: #ebf5fb;">
    <td><b>Role</b></td>
    <td><b>Access Level</b></td>
  </tr>
  <tr style="background-color: #f7fbfe;">
    <td>Senior Planner</td>
    <td>Read/Write: Logistics, Clients, Decision Log.</td>
  </tr>
  <tr style="background-color: #ebf5fb;">
    <td>Operations Manager</td>
    <td>Administrative: Vendors, Employees, Appointments.</td>
  </tr>
  <tr style="background-color: #f7fbfe;">
    <td>Admin Assistant</td>
    <td>Specialized: Contracts and Status management.</td>
  </tr>
</table>

---

### Repository Structure

* **/docs:** Full Proposal PDF and Technical Documentation.
* **/scripts:** SQL scripts for schema creation and 3NF implementation.
* **/scripts/views.sql:** Saved views and sample queries.
* **/data:** Seed data for demonstration purposes, including mock clients, vendors, services, actual employees, and statuses aligned with expected system behavior.

---

### License

This project is licensed under the [MIT License](https://github.com/kwplead112245/Elegant_Occasions_DB_Proposal/blob/main/LICENSE).

<div align="center">
  <sub>Developed by <b>Katy Warren-Parker</b> | <a href="mailto:katywarrenparker@students.abtech.edu">Contact Me</a></sub>
</div>
