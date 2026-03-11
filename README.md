<h1 align="center">🏥 Clinic Management</h1>

<p align="center">
  <strong>Desktop Clinic Management System</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white" />
  <img src="https://img.shields.io/badge/ADO.NET-512BD4?style=flat-square&logo=dotnet&logoColor=white" />
  <img src="https://img.shields.io/badge/.NET-512BD4?style=flat-square&logo=dotnet&logoColor=white" />
</p>

---

## 📌 About

Clinic Management is a desktop application for managing patient records and appointment scheduling in a simulated clinic environment. Built with **C#** and **ADO.NET**, it connects to a **SQL Server** database through a **normalized relational schema** with **parameterized queries** to prevent SQL injection.

---

## ⚙️ Tech Stack

| Layer | Technology |
|:------|:-----------|
| **Language** | C# |
| **Database** | SQL Server |
| **Data Access** | ADO.NET |
| **UI** | Windows Forms |
| **Security** | Parameterized queries (SQL injection prevention) |

---

## 🚀 Features

- **Patient Records** — Full CRUD for patient information
- **Appointment Scheduling** — Book, update, and cancel appointments
- **Normalized Schema** — Properly structured relational database design
- **Secure Queries** — All database calls use parameterized queries to prevent SQL injection
- **ADO.NET Connectivity** — Direct, efficient database access without ORM overhead

---

## 🗄️ Database

The database uses a normalized relational schema designed for a clinic environment:

```
┌──────────────┐     ┌──────────────────┐
│   Patients   │     │   Appointments   │
├──────────────┤     ├──────────────────┤
│ PatientId    │◄───►│ AppointmentId    │
│ Name         │     │ PatientId (FK)   │
│ DOB          │     │ DateTime         │
│ Phone        │     │ Status           │
│ Email        │     │ Notes            │
│ Address      │     └──────────────────┘
└──────────────┘
```

---

## 📦 Getting Started

### Prerequisites

- .NET SDK
- SQL Server (LocalDB or SQLEXPRESS)
- Visual Studio 2022

### Setup

1. Clone the repo
   ```bash
   git clone https://github.com/safwan-islam/Clinic-Management.git
   ```
2. Open the solution in Visual Studio
3. Create the database using the provided SQL scripts
4. Update the connection string in the project configuration
5. Build and run

---

## 👤 Author

**Safwan-Ahmed Islam** — [GitHub](https://github.com/safwan-islam) · [LinkedIn](https://linkedin.com/in/safwan-islam)
