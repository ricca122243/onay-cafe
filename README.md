# OnaıCafe
## MASTER PROJECT README & PRODUCT SPECIFICATION

**Project Type:** QR-Based Restaurant Ordering and Payment Platform  
**Project Name:** OnaıCafe  
**Target Market:** Kazakhstan  
**Project Stage:** Product Discovery & Architecture  
**Document Status:** Initial Draft — Requires AI Audit and Human Approval

---

# 1. PROJECT OVERVIEW

OnaıCafe is a digital restaurant management and ordering platform designed to simplify the traditional restaurant service process.

The platform allows customers to independently browse menus, select food, place orders, and pay using their smartphones.

The main interaction happens through a QR code placed on each restaurant table.

Instead of waiting for a waiter to bring a menu, take an order, and process payment, customers can complete most of these actions independently.

The restaurant receives orders digitally and processes them through a centralized order management system.

The waiter's primary responsibility becomes delivering prepared orders to the correct tables.

OnaıCafe aims to reduce unnecessary manual operations, optimize restaurant staffing expenses, minimize human errors, and improve customer experience.

**IMPORTANT:** This is our initial product vision, not a finalized technical specification. You must critically evaluate and improve it.

# 2. THE PROBLEM WE WANT TO SOLVE

Traditional restaurant service often involves several repetitive operations:

1. A customer enters the restaurant.
2. A waiter approaches the table.
3. The waiter provides the menu.
4. The customer selects food.
5. The waiter manually takes the order.
6. The waiter communicates the order to the kitchen.
7. The customer waits for preparation.
8. The waiter brings the bill.
9. The customer pays.
10. The waiter or cashier processes the payment.

This workflow requires significant staff involvement.

Potential problems:

- Customers wait too long for service.
- Waiters spend time taking repetitive orders.
- Orders can be misunderstood.
- Communication between waiters and kitchen staff can be inefficient.
- Restaurant operating expenses increase.
- During peak hours, staff may become overloaded.
- Manual payment processes can slow down table turnover.

OnaıCafe aims to automate the repetitive digital parts of this process.

# 3. PRODUCT VISION

Our vision is to create a convenient digital ordering ecosystem for cafes and restaurants in Kazakhstan.

A customer should be able to:

- Sit at a restaurant table.
- Scan a QR code.
- Open the digital menu.
- Browse food and beverages.
- View photographs, ingredients, descriptions, and prices.
- Add products to a cart.
- Customize products where supported.
- Confirm an order.
- Pay through an officially supported payment solution.
- Track order progress.
- Receive their food at the table.

Restaurant employees should receive organized information without manually transferring every order.

# 4. CUSTOMER JOURNEY

Analyze and improve the following workflow.

## STEP 1 — Entering the restaurant

The customer enters the cafe and chooses a table.

Each table has a unique QR code.

The QR code should identify:

- Restaurant.
- Branch.
- Table.
- Relevant ordering session, if required.

Evaluate whether QR codes should be static, dynamic, signed, or session-based.

Consider security risks such as copied QR codes and incorrect table identification.

## STEP 2 — Scanning the QR code

The customer scans the QR code using their smartphone camera.

The browser opens the OnaıCafe web application.

The customer should not need to install a mobile application.

The system identifies the restaurant and table automatically.

Determine how to prevent customers from submitting orders for another table.

## STEP 3 — Digital menu

The customer sees:

- Restaurant branding.
- Food categories.
- Food photographs.
- Product names.
- Descriptions.
- Prices.
- Availability.
- Customization options.
- Search and filtering.

The menu must be responsive and mobile-first.

Consider usability for customers with different levels of technical experience.

## STEP 4 — Shopping cart

Customers can:

- Add products.
- Remove products.
- Change quantities.
- Select product variations.
- Add special instructions.
- Review the total price.

The backend must validate product prices and availability.

Never trust prices sent directly from the frontend.

## STEP 5 — Order confirmation

Before payment, display:

- Restaurant and branch.
- Table number.
- Selected products.
- Quantities.
- Product modifications.
- Subtotal.
- Additional charges, if applicable.
- Final amount.

Evaluate whether the restaurant should support:

- Minimum order amounts.
- Service fees.
- Discounts.
- Promotional codes.
- Special requests.

## STEP 6 — Payment

The customer chooses an available payment method.

Our initial target is integration with Kaspi.

However, do not assume that any particular Kaspi API, redirect flow, QR payment method, or merchant integration is available.

Research official payment integration documentation.

Identify:

- Supported payment methods.
- Merchant requirements.
- Payment confirmation mechanisms.
- Webhook support.
- Refund capabilities.
- Transaction status retrieval.
- Integration restrictions.

If direct integration is unavailable, recommend a realistic alternative.

A critical requirement:

Returning to the website after opening a payment application must NEVER automatically mean that the order has been paid.

The backend must verify payment through a trusted provider confirmation mechanism.

## STEP 7 — Order registration

After payment is successfully verified:

- Confirm the order.
- Save the transaction reference.
- Save the order items and prices.
- Record the table.
- Record the order creation time.
- Notify the relevant restaurant system.

Prevent duplicate orders and duplicate payment processing.

Consider idempotency and transaction consistency.

## STEP 8 — Kitchen workflow

The kitchen receives the order through a dashboard or supported notification system.

The kitchen interface should display:

- Order number.
- Table number.
- Ordered products.
- Quantities.
- Customizations.
- Special instructions.
- Order creation time.
- Current status.

Kitchen employees should be able to update statuses.

Evaluate whether different kitchen stations are needed for drinks, hot food, desserts, etc.

## STEP 9 — Waiter workflow

The waiter sees orders that are ready for delivery.

The interface should identify:

- Table number.
- Order number.
- Ready status.
- Delivery details.

The waiter brings the prepared order to the correct table.

Evaluate whether the waiter should confirm delivery through the application.

## STEP 10 — Completed order

After delivery, the order becomes completed or served.

The system saves the order history.

The customer may optionally provide feedback.

# 5. RESTAURANT USER ROLES

Analyze and define a proper role-based access control system.

Potential roles:

### CUSTOMER

- Browse menu.
- Create cart.
- Submit order.
- Pay.
- Track order.
- View their current order.

### WAITER

- View assigned tables.
- View ready orders.
- Deliver orders.
- Confirm delivery.
- Report problems.

### KITCHEN STAFF

- View incoming orders.
- Accept orders.
- Start preparation.
- Mark orders as ready.
- View preparation instructions.

### CASHIER

- Monitor orders and payments.
- Verify transaction statuses.
- Handle supported payment operations.
- Assist with order problems.

### RESTAURANT ADMINISTRATOR

- Manage menu.
- Manage categories.
- Manage products.
- Manage prices.
- Manage tables.
- Manage employees.
- View orders.
- View reports.

### SUPER ADMINISTRATOR

- Manage restaurants.
- Manage branches.
- Manage platform-level settings.
- Monitor system health.
- Manage subscriptions if the SaaS model is implemented.

Determine whether all these roles are necessary for the MVP.

# 6. RESTAURANT ADMINISTRATOR PANEL

The administrator should be able to manage restaurant operations.

Potential capabilities:

- Create and edit food categories.
- Add and remove products.
- Upload photographs.
- Change prices.
- Control product availability.
- Manage table numbers.
- Generate QR codes.
- Manage employee accounts.
- Assign employee roles.
- Monitor active orders.
- View payment history.
- View revenue reports.
- Configure restaurant information.

Evaluate the required dashboard sections and prioritize them.

# 7. KITCHEN ORDER MANAGEMENT

Design a dedicated kitchen interface.

It should support:

- Incoming orders.
- Accepted orders.
- Orders being prepared.
- Ready orders.
- Completed orders.

The interface should be optimized for large screens and touch devices.

Consider real-time updates using an appropriate technology.

Recommend whether WebSockets, Server-Sent Events, polling, or another mechanism is suitable.

Do not add unnecessary infrastructure.

# 8. CORE BUSINESS LOGIC

This section requires particularly careful analysis.

Investigate every possible inconsistency.

Questions to resolve:

1. What happens if the customer scans a QR code but leaves?
2. What happens if a customer changes tables?
3. What happens if the QR code is copied?
4. What happens if a product becomes unavailable after being added to the cart?
5. What happens if prices change during checkout?
6. What happens if payment succeeds but the browser closes?
7. What happens if payment fails?
8. What happens if payment confirmation arrives twice?
9. What happens if the kitchen does not accept an order?
10. What happens if the restaurant closes while an order is being created?
11. What happens if the customer orders the same product twice?
12. What happens if the internet connection is interrupted?
13. What happens if the kitchen marks an order ready by mistake?
14. What happens if the waiter delivers an order to the wrong table?
15. What happens if a customer requests cancellation after payment?

For each situation, propose a reliable solution.

Document all decisions.

# 9. ORDER STATUS ARCHITECTURE

Evaluate this initial status model:

- DRAFT
- PENDING_PAYMENT
- PAYMENT_FAILED
- PAID
- ACCEPTED
- PREPARING
- READY
- SERVED
- CANCELLED
- REFUND_PENDING
- REFUNDED

Do not assume this list is optimal.

Consider separating payment status from order status.

For example:

Order status:
- PENDING
- CONFIRMED
- ACCEPTED
- PREPARING
- READY
- SERVED
- CANCELLED

Payment status:
- UNPAID
- PENDING
- PAID
- FAILED
- REFUND_PENDING
- REFUNDED

Explain the advantages of separating these state machines.

# 10. TECHNICAL ARCHITECTURE

Evaluate the following proposed technologies:

Frontend:
- Next.js
- React
- TypeScript
- Tailwind CSS

Backend:
- Next.js server-side architecture
- API routes or Route Handlers
- Service layer
- Validation with Zod

Database:
- PostgreSQL
- Prisma ORM

Authentication:
- Auth.js or an appropriate alternative

Testing:
- Vitest
- Playwright

Version Control:
- Git
- GitHub

Deployment:
- Recommend a suitable hosting and deployment strategy.

Payments:
- Officially supported Kaspi integration, subject to verification.

Evaluate the entire stack.

Explain whether a modular monolith is more appropriate than microservices for our initial stage.

Prefer the simplest architecture that supports future growth.

# 11. DATABASE DESIGN

Design and evaluate the database entities.

Initial candidates:

- User
- Restaurant
- Branch
- Table
- QRCode
- Category
- Product
- ProductVariant
- ProductImage
- Order
- OrderItem
- Payment
- PaymentEvent
- OrderStatusHistory
- Employee
- Role
- RestaurantSettings

For each entity, define:

- Purpose.
- Fields.
- Data types.
- Primary keys.
- Foreign keys.
- Relationships.
- Constraints.
- Indexes.

Consider multi-tenant isolation so one restaurant cannot access another restaurant's data.

Do not create unnecessary entities without explaining why they are needed.

Prepare a complete proposed Prisma schema, but wait for human approval before implementation.

# 12. SECURITY AND RELIABILITY

Analyze:

- Authentication.
- Authorization.
- QR code security.
- Input validation.
- SQL injection prevention.
- XSS protection.
- CSRF protection where applicable.
- Payment verification.
- Webhook signature verification.
- Rate limiting.
- Duplicate order prevention.
- Restaurant data isolation.
- Secrets management.
- Audit logs.
- Backup strategy.

Treat payment processing as a high-priority security area.

Never store bank card details or sensitive payment credentials in our own database.

# 13. BUSINESS MODEL

Evaluate possible business models:

- Monthly SaaS subscription for restaurants.
- Subscription based on number of branches.
- Subscription based on number of tables.
- Fixed monthly fee.
- Additional paid modules.

Analyze whether OnaıCafe should initially serve one restaurant or be built as a multi-restaurant platform.

Recommend an MVP business model.

Do not invent market statistics. Mark estimates as assumptions.

# 14. MVP SCOPE

Separate features into three groups.

### MUST HAVE

Features required for the first usable product.

### SHOULD HAVE

Features that improve the product but are not essential for launch.

### FUTURE

Advanced functionality for later versions.

Avoid unnecessary complexity in the MVP.

# 15. TWO-AGENT DEVELOPMENT ARCHITECTURE

Two developers work on the same OnaıCafe project using separate Claude Code sessions.

The repository and documentation are shared through GitHub.

CLAUDE A — BACKEND AGENT

Responsibilities:

- Database.
- Prisma.
- Server logic.
- API.
- Authentication.
- Authorization.
- Order management.
- Payment logic.
- Backend testing.

CLAUDE B — FRONTEND AGENT

Responsibilities:

- UI/UX.
- Design system.
- Responsive components.
- Customer website.
- Menu.
- Cart.
- Checkout interface.
- Kitchen dashboard.
- Waiter dashboard.
- Administrator dashboard.
- Frontend testing.

Both agents must read the same root CLAUDE.md.

Both agents must use shared API contracts.

Both agents must respect the same architecture.

Both agents must update relevant documentation.

Neither agent may independently change approved architecture.

Use feature branches and Pull Requests.

Never assume that another Claude session can see uncommitted files from another computer.

# 16. REQUIRED PROJECT DOCUMENTATION

Create and maintain:

README.md
CLAUDE.md

docs/
  PROJECT_OVERVIEW.md
  PRODUCT_REQUIREMENTS.md
  ARCHITECTURE.md
  DATABASE.md
  API_CONTRACTS.md
  BUSINESS_LOGIC.md
  PAYMENT_FLOW.md
  SECURITY.md
  DESIGN_SYSTEM.md
  DEVELOPMENT_RULES.md
  TASK_BOARD.md
  DECISIONS.md
  ROADMAP.md

All documents must agree with one another.

If an architectural decision changes, update every affected document.

# 17. DEVELOPMENT RULES

Follow these rules:

1. Inspect before modifying.
2. Understand before implementing.
3. Plan before coding.
4. Respect existing architecture.
5. Avoid unnecessary dependencies.
6. Avoid duplicated logic.
7. Use strict TypeScript.
8. Validate external input.
9. Handle errors explicitly.
10. Test important business logic.
11. Update documentation.
12. Never expose secrets.
13. Never claim functionality is implemented if it is not.
14. Never use mock payment success as real payment confirmation.
15. Never silently change public API contracts.

# 18. YOUR REQUIRED AUDIT

Act as a critical senior architect.

Do not simply rewrite our initial idea.

Find problems.

Identify missing business processes.

Identify incorrect assumptions.

Find unnecessary complexity.

Identify security risks.

Identify operational problems.

Recommend improvements.

For every identified issue, provide:

- Problem.
- Why it matters.
- Potential consequences.
- Recommended solution.
- Priority: Critical / High / Medium / Low.

# 19. REQUIRED EXECUTION ORDER

Work in the following phases.

PHASE 1 — PRODUCT DISCOVERY

Understand and analyze the complete idea.

PHASE 2 — LOGICAL AUDIT

Find missing workflows, contradictions, risks, and weaknesses.

PHASE 3 — PRODUCT IMPROVEMENT

Propose a better version of OnaıCafe.

PHASE 4 — ARCHITECTURE DESIGN

Define system boundaries, modules, data flows, and integrations.

PHASE 5 — DATABASE AND API DESIGN

Prepare proposed models and contracts.

PHASE 6 — MVP DEFINITION

Define the minimum usable product.

PHASE 7 — TWO-AGENT COORDINATION

Define responsibilities, documentation, Git workflow, and task management.

PHASE 8 — DOCUMENTATION

Prepare the shared project documentation.

PHASE 9 — HUMAN REVIEW

Present all important decisions for approval.

Do not begin full implementation before approval.

# 20. FIRST RESPONSE REQUIREMENTS

Before modifying the repository, provide:

1. Your understanding of OnaıCafe.
2. Your critical assessment of the idea.
3. At least ten potential logical problems, if applicable.
4. Missing business workflows.
5. Recommended product improvements.
6. Recommended technology architecture.
7. Proposed database structure.
8. Recommended order and payment flows.
9. MVP feature list.
10. Two-agent development strategy.
11. Decisions that require approval from the developers.

Be honest, technically precise, and critical.

Your goal is not to make our initial idea sound good.

Your goal is to make OnaıCafe logically correct, technically feasible, secure, maintainable, and commercially useful.

**We want to build a real product, not just a demonstration website.**
