# Problem Statement

## 1. Title
Smart Split & Group Wallet System

## 2. Domain
FinTech / Personal Expense Management

## 3. Who is the user? (2-3 user types, with roles)
1. **Group Admin**: Creates and manages expense groups, invites members, manages group wallet permissions, and approves balance settlements.
2. **Group Member**: Deposits funds into group wallets, logs shared expenses, splits bills with other members, and settles balances.
3. **System Admin**: Manages overall platform health, oversees global user accounts, monitors transaction logs, and reviews audit reports.

## 4. What problem are we solving? (3-5 sentences, real-life example)
When roommates share household bills, colleagues order team lunches, or friends go on a vacation, keeping track of shared expenses quickly becomes chaotic and error-prone. Manual calculations across spreadsheets or chat messages often lead to forgotten debts, miscalculated split shares, and awkward payment reminders. Furthermore, settling multiple individual small debts creates unnecessary financial clutter with dozens of micro-transfers between friends. Existing basic split utilities lack centralized group wallets to pre-fund shared trip budgets and fail to automatically minimize multi-person debt transactions.

## 5. Proposed Solution (what the application will do, feature-wise)
A full-stack web application that allows users to create budget groups, manage virtual group wallets, log multi-member expenses, and streamline settlements.
Key features include:
- **Group Wallet Management**: Pre-fund group wallets for shared outings or living expenses.
- **Flexible Expense Splitting**: Log expenses with Equal, Percentage, or Exact-Amount split strategies.
- **Smart Debt Minimization Algorithm**: Backend Java algorithm that automatically simplifies multi-person debt graphs to minimize the number of required payout transactions.
- **Settlement & Payment Gateway Sandbox**: Integrated test-mode payment gateway to clear pending dues directly inside the platform.
- **Audit Ledger & Reports**: Real-time statement history, group balance dashboards, and exportable financial summaries.

## 6. Core Entities / Database Tables (list all, minimum 5)
1. `User` (id, full_name, email, password_hash, role, created_at)
2. `ExpenseGroup` (id, name, description, created_by_user_id, wallet_balance, currency, created_at)
3. `GroupMember` (id, group_id, user_id, member_role, joined_at)
4. `Expense` (id, group_id, paid_by_user_id, total_amount, description, split_type, category, created_at)
5. `ExpenseSplit` (id, expense_id, user_id, amount_owed, is_settled)
6. `Settlement` (id, group_id, payer_id, payee_id, amount, payment_status, transaction_reference, created_at)
7. `WalletTransaction` (id, group_id, user_id, transaction_type, amount, balance_after, created_at)

## 7. User Roles & Permissions (minimum 2 distinct roles, e.g. Admin & User)
- **Group Admin**: 
  - Full permissions to edit group details, invite/remove group members, and archive groups.
  - Can manage group wallet rules and override disputed expense items.
- **Group Member**: 
  - Can view group dashboards, contribute funds to group wallet pools, create expenses, assign split shares, and execute balance settlements.
- **System Admin**: 
  - Read-only or full administrative privileges across all system tables for platform auditing, system monitoring, and user management.

## 8. Success Criteria (e.g. 'a user should be able to book an appointment in under 1 minute')
- A user should be able to log a complex bill split among 5 people in under 30 seconds.
- The debt minimization engine must reduce a multi-debt cycle (e.g., 6 cross-member debts) into the minimum possible direct transactions.
- Group wallet ledger balances must stay 100% accurate without balance discrepancies during concurrent spending.

## 9. Out of Scope (clearly list what you will NOT build, to avoid over-commitment)
- Live banking integration via actual banking APIs (uses simulated payment sandbox).
- Multi-currency real-time foreign exchange conversion rates.
- Native mobile applications for iOS/Android (desktop and mobile responsive web application only).

## 10. Chosen Track: Java (Spring Boot)

