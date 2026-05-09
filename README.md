# Vision Valley Attendance System — Back-End

A comprehensive **ASP.NET Core MVC + REST API** system for managing employee attendance across organizations — with smart device integration, IoT lamp control, face recognition, real-time notifications via SignalR, and timetable-based scheduling.

## What it does

Vision Valley is an end-to-end attendance management platform. Employees check in/out via registered devices (tablets/terminals). The system validates attendance against configured timetables, supports face biometric verification, controls IoT smart lamps, and provides a full web dashboard for admins to manage branches, departments, users, and attendance reports.

## Key Features

- **Device-based Attendance** — Physical devices (terminals) registered per branch record check-ins/outs
- **Timetable Scheduling** — Define work schedules per employee/department; attendance is validated against the timetable
- **Face Recognition** — Enroll user face images and verify identity on check-in via an external Python face API
- **IoT Lamp Control** — Manage smart lamps per room; lamps can be scheduled and controlled via WebSocket; access requests supported
- **Real-time Notifications** — SignalR hub pushes live alerts to connected clients
- **Multi-Organization / Branch / Department** — Full hierarchy: Organization → Branch → Department → User
- **Attendance Reports** — Generate and export PDF attendance reports per user, team, or branch
- **Manual Attendance** — Admins can manually create or correct attendance records
- **MVC Dashboard** — Full admin web UI with Bootstrap styling
- **REST API** — Separate API controllers for mobile/device clients

## Tech Stack

- ASP.NET Core 8 (MVC + Web API)
- Entity Framework Core + SQL Server
- ASP.NET Identity + JWT Bearer
- SignalR (real-time WebSocket notifications)
- DinkToPdf (PDF export)
- External Python Face Recognition API

## Architecture

```
CoreProject/    → Models, Services, Repositories, ViewModels, Interfaces (shared library)
MvcCoreProject/ → ASP.NET MVC web app (views, controllers, SignalR hubs, middleware)
```

## Main Modules

| Module | Description |
|---|---|
| **Auth** | Login, role-based access (Admin, Manager, Employee) |
| **Users** | Create, manage, assign roles, enroll face images |
| **Branches** | Physical office locations |
| **Departments** | Team groupings within branches |
| **Devices** | Registered check-in terminals per branch |
| **Timetables** | Work schedule configurations |
| **Attendance** | Check-in/out records, reports, manual entries |
| **Lamps** | IoT smart lamp management with scheduling & access requests |
| **Dashboard** | Stats overview (present/absent/late counts, etc.) |

## Getting Started

1. Set the SQL Server connection string in `appsettings.json`
2. Configure JWT and face API settings
3. Run: `dotnet ef database update`
4. Run `MvcCoreProject` as the startup project
5. Log in with the seeded admin account and begin setup
