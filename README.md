# Dental Clinic Management System

An offline-first desktop management system for dental clinics, designed for daily front-desk and doctor workflows: patients, appointments, a live waiting queue, and a waiting-room display screen.

> **Note:** This is a production system built for a real clinic, so the source code is kept in a private repository. This page documents the product and its architecture.

![System overview: doctor client and reception server synced in real time over the local network](docs/screenshots/system-overview.jpg)

## Highlights

- **Patients and appointments**: patient registration and search, booking, rescheduling and cancelling, check-in with queue numbers and booking codes
- **Live queue**: one-click "call next patient" alerts that reach the doctor, the secretary and a waiting-room TV display in real time over the local network
- **Role-based access**: separate Doctor and Secretary roles, user account management, and an audit log for sensitive actions
- **Built to survive power cuts**: draft notes auto-save while typing, crash recovery after power loss, and automatic local backups
- **Arabic-first**: right-to-left interface designed from the start, not translated afterwards
- **Fast for repeat tasks**: the most common actions (check-in, call, record a payment) take one or two clicks

## Screenshots

![Waiting-room TV display showing the current and upcoming queue numbers](docs/screenshots/waiting-room-display.jpg)

## Architecture

| Layer | Technology |
| --- | --- |
| Desktop shell | Electron |
| Front end | React, TypeScript |
| Local server | Node.js, TypeScript (runs inside the desktop app) |
| Database | PostgreSQL (local instance), Prisma |
| Realtime | WebSocket |
| Cloud layer | Supabase (public website, online booking, cloud backup) |
| Waiting-room display | Lightweight web page connected over the local network |
| Tooling | pnpm workspaces monorepo, ESLint, Prettier |

One workstation acts as the local server and the other devices connect to it as clients, so the clinic keeps working even without an internet connection.

```
apps/
  desktop/    Electron app: main process, local server, React UI
  display/    Waiting-room TV display
packages/
  db/            Database schema and migrations
  shared-types/  TypeScript types shared across apps
```

## Related Projects

- [Dental Clinic Website](https://github.com/salmantawfeeq/dental-clinic-website): the public Arabic-first clinic website with online booking (Next.js, TypeScript, Supabase) - [live demo](https://salmantawfeeq.github.io/dental-clinic-website/)

## Status

In active development and in use by the clinic.

## Author

**Salman Tawfiq** - Full-Stack Software Engineer, Riyadh, Saudi Arabia
[LinkedIn](https://www.linkedin.com/in/salmantawfiq) | [Portfolio](https://salmantawfiq.com)
