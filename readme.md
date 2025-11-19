# Uptime Monitor

A robust, full-stack uptime monitoring solution designed to keep track of your services' health, manage incidents, and communicate status to your users.

## 🚀 Features

-   **Real-time Monitoring**: HTTP/HTTPS monitoring with customizable intervals and timeout settings.
-   **Incident Management**: Track and manage service outages with detailed incident reports.
-   **Status Pages**: Public-facing status pages to keep your users informed.
-   **Multi-Channel Notifications**: Get alerted via Email (more channels coming soon).
-   **Team Collaboration**: Invite team members to manage monitors and incidents.
-   **Subscription Management**: Integrated pricing and subscription handling.

## 🛠️ Tech Stack

This project is built as a monorepo with two main components:

### 1. Web Application (`uptime-monitor`)
-   **Framework**: [Next.js 15](https://nextjs.org/) (App Router)
-   **Language**: TypeScript
-   **Styling**: Tailwind CSS, Shadcn UI
-   **Database ORM**: Drizzle ORM
-   **API**: tRPC
-   **Auth**: Better Auth / Polar.sh
-   **State Management**: TanStack Query

### 2. Monitor Worker (`monitor-check-worker`)
-   **Runtime**: Node.js
-   **Queue**: BullMQ
-   **Storage**: Redis
-   **HTTP Client**: Axios
-   **Database**: Drizzle ORM (Shared DB access)

## 📂 Project Structure

```
.
├── uptime-monitor/       # Next.js web application
│   ├── src/              # Source code
│   ├── public/           # Static assets
│   └── ...
└── monitor-check-worker/ # Background worker service
    ├── src/              # Worker source code
    └── ...
```

## 🏁 Getting Started

### Prerequisites

Ensure you have the following installed:
-   [Node.js](https://nodejs.org/) (v18+ recommended)
-   [Bun](https://bun.sh/) (Required for worker scripts)
-   [PostgreSQL](https://www.postgresql.org/)
-   [Redis](https://redis.io/)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd uptime-monitor-project
    ```

2.  **Install dependencies:**

    For the web app:
    ```bash
    cd uptime-monitor
    npm install
    ```

    For the worker:
    ```bash
    cd ../monitor-check-worker
    npm install
    ```

### Configuration

You will need to set up environment variables for both services.

1.  **Web App (`uptime-monitor/.env`):**
    Copy the example env file (if available) or create a `.env` file with:
    ```env
    DATABASE_URL="postgresql://user:password@localhost:5432/uptime_db"
    # Add other required vars found in src/env.js
    ```

2.  **Worker (`monitor-check-worker/.env`):**
    Create a `.env` file with:
    ```env
    DATABASE_URL="postgresql://user:password@localhost:5432/uptime_db"
    REDIS_URL="redis://localhost:6379"
    # Add other required vars
    ```

### Running the Application

You need to run both the web application and the worker service.

**1. Start the Web App:**
```bash
cd uptime-monitor
npm run dev
```
The app will be available at `http://localhost:3000`.

**2. Start the Worker:**
```bash
cd monitor-check-worker
npm run dev
```
The worker will start processing monitoring jobs from the queue.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

[MIT](LICENSE)
