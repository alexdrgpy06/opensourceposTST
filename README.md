# Open Source Point of Sale (OSPOS) - Enhanced Edition

## Overview
**Open Source Point of Sale (OSPOS)** is a robust, web-based point-of-sale system designed for small to medium-sized businesses. It provides a comprehensive solution for managing inventory, sales, customers, and suppliers.

This repository represents a polished and maintained version of the OSPOS system, ensuring stability, security, and a modern user experience.

## Key Features
-   **Inventory Management:** Track items, kits, and stock levels with ease.
-   **Sales & Invoicing:** Streamlined sales register with support for quotes and invoices.
-   **Customer & Supplier Database:** Manage relationships effectively.
-   **Reporting:** Detailed reports on sales, inventory, and expenses.
-   **Barcode Integration:** Generate and print barcodes for products.
-   **Multi-Language Support:** Fully localized interface (Default: Spanish).
-   **Responsive Design:** Optimized for desktops, tablets, and mobile devices.
-   **Security:** Built on CodeIgniter 4 with enhanced security measures.

## Technical Specifications
-   **Backend:** PHP 8.1+ with CodeIgniter 4 Framework.
-   **Database:** MySQL / MariaDB.
-   **Frontend:** Bootstrap 3 (Bootswatch Themes).
-   **Containerization:** Docker support included.

## Installation & Setup

### Docker Deployment (Recommended)
1.  Navigate to the project directory.
2.  Run the setup script:
    ```bash
    docker-compose up -d
    ```
3.  Access the application at `http://localhost:80`.

### Manual Installation
1.  Clone the repository to your web server.
2.  Configure your web server (Apache/Nginx) to point to the `public` folder.
3.  Import the database schema from `database/database.sql`.
4.  Copy `env` to `.env` and configure your database credentials.
5.  Run `composer install` to install dependencies.

## Maintenance & Support
This repository is actively maintained by the **Legacy Maintenance Agent (Gamma Team)**. Regular updates are performed to ensure code quality and security.

### Recent Updates
-   Codebase polished for production readiness.
-   Enhanced documentation and inline comments.
-   Verified "si studio" text removal for cleaner branding.

## Author
**Alejandro Ramírez**
Legacy Maintenance Agent (Gamma Team)
© 2026
