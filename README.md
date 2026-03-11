<h1 align="center">🏥 Clinic Management</h1>

<p align="center">
  <strong>SantePlus — Desktop Clinic Management System</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white" />
  <img src="https://img.shields.io/badge/.NET_Framework-512BD4?style=flat-square&logo=dotnet&logoColor=white" />
  <img src="https://img.shields.io/badge/SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white" />
  <img src="https://img.shields.io/badge/ADO.NET-512BD4?style=flat-square&logo=dotnet&logoColor=white" />
  <img src="https://img.shields.io/badge/Windows_Forms-0078D4?style=flat-square&logo=windows&logoColor=white" />
</p>

---

## 📌 About

SantePlus is a desktop clinic management system built with a **3-tier architecture** (UI / BLL / DAL). It manages patients, doctors, appointments, consultations, schedules, and reports for a simulated healthcare clinic. The system supports 3 user roles — **Administrateur**, **Médecin**, and **Réceptionniste** — each with a dedicated Windows Forms interface.

The database layer uses **ADO.NET with parameterized queries** to prevent SQL injection, plus **stored procedures** for appointment booking, availability checks, patient history, and monthly report generation.

---

## ⚙️ Tech Stack

| Layer | Technology |
|:------|:-----------|
| **Language** | C# |
| **Framework** | .NET Framework 4.7.2 |
| **Database** | SQL Server (10 tables, 2 views, 4 stored procedures) |
| **Data Access** | ADO.NET (parameterized queries) |
| **UI** | Windows Forms |
| **Architecture** | 3-Tier (UI / BLL / DAL) |

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────┐
│                      UI Layer                         │
│  AuthentificationForm                                 │
│  AdministrateurForm                                   │
│  MedecinForm → GestionsConsultationsForm              │
│              → HistoriquePatientForm                  │
│  ReceptionnisteForm → GestionRendezVousReceptForm     │
│  GestionPatientsForm                                  │
│  GestionMedecinsForm                                  │
│  GestionHorairesForm                                  │
│  GestionRapportsForm                                  │
│  GestionReceptionnistesForm                           │
├──────────────────────────────────────────────────────┤
│                  Business Layer (BLL)                  │
│  Patient, Medecin, Consultation, RendezVous,          │
│  Horaire, Receptionniste, Rapport, Utilisateur,       │
│  Authentification                                     │
├──────────────────────────────────────────────────────┤
│                   Data Layer (DAL)                     │
│  DatabaseConnection                                   │
│  PatientDB, MedecinDB, ConsultationDB,                │
│  RendezVousDB, HoraireDB, ReceptionnisteDB,           │
│  RapportDB, UtilisateurDB, AuthentificationDB         │
│  View_PatientRendezVous, View_Consultation            │
├──────────────────────────────────────────────────────┤
│               SQL Server (SantePlusDB)                │
└──────────────────────────────────────────────────────┘
```

---

## 🗄️ Database

### Tables (10)

| Table | Description |
|:------|:------------|
| `Patient` | Patients (name, address, phone, DOB) |
| `Medecin` | Doctors (name, specialty, availability) |
| `RendezVous` | Appointments (date, time, patient FK, doctor FK, status) |
| `Consultation` | Visit records (diagnosis + prescription) |
| `Horaire` | Weekly schedules (day, start/end time) |
| `Medecin_Horaire` | Many-to-many: doctor ↔ schedule |
| `Administrateur` | Admin profiles |
| `Receptionniste` | Receptionist profiles |
| `Utilisateur` | System users |
| `Authentification` | Login credentials (login, password, role) |
| `Utilisateur_Authentification` | Many-to-many: user ↔ auth |
| `Rapport` | Monthly reports (appointment count, occupancy rate) |

### Views (2)

| View | Joins |
|:-----|:------|
| `View_PatientRendezVous` | Patient + RendezVous + Medecin |
| `View_Consultation` | Consultation + Patient + Medecin |

### Stored Procedures (4)

| Procedure | What it does |
|:----------|:-------------|
| `PlanifierRendezVous` | Books an appointment with status "Planned" |
| `ConsulterDisponibiliteMedecin` | Returns a doctor's available schedule slots |
| `VerifierDisponibiliteMedecin` | Checks for double-booking before creating an appointment |
| `HistoriquePatient` | Returns full visit history (appointments + consultations) |
| `GenererRapportMensuel` | Generates monthly report per doctor (appointment count, hours worked) |

### Constraints

- `UQ_MedecinDateHeure` — Prevents double-booking a doctor at the same date/time

---

## 🔐 Role-Based Access

Each role gets a dedicated Windows Form after login:

| Role | Form | Access |
|:-----|:-----|:-------|
| **Administrateur** | `AdministrateurForm` | Manage patients, doctors, receptionists, schedules, reports |
| **Médecin** | `MedecinForm` | Consultations, patient history |
| **Réceptionniste** | `ReceptionnisteForm` | Appointment booking and management |

---

## 📦 Getting Started

### Prerequisites

- .NET Framework 4.7.2
- SQL Server
- Visual Studio 2022

### Setup

1. Clone the repo
   ```bash
   git clone https://github.com/safwan-islam/Clinic-Management.git
   ```
2. Run `CliniqueSantePartie3.sql` in SSMS to create the `SantePlusDB` database with all tables, seed data, views, and stored procedures
3. Open the solution in Visual Studio
4. Update the connection string in `DatabaseConnection.cs`
5. Build and run

### Default Credentials

| Login | Password | Role |
|:------|:---------|:-----|
| `admin` | `admin123` | Administrateur |
| `pierre.leclerc` | `medecin123` | Médecin |
| `claire.lemoine` | `reception123` | Réceptionniste |

---

## 👤 Author

**Safwan-Ahmed Islam** — [GitHub](https://github.com/safwan-islam) · [LinkedIn](https://linkedin.com/in/safwan-islam)
