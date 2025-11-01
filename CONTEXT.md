# HiyoRi E-commerce with Cashback Platform

## 1. Project Overview
A comprehensive e-commerce platform with integrated cashback and wallet functionality, built with Next.js and Supabase. The project combines the core e-commerce features from HiyoRi with advanced cashback and wallet management from the cashback-commerce project.

### Core Features
- **E-commerce Platform** (from HiyoRi)
  - Product catalog and search
  - Shopping cart and checkout
  - User authentication
  - Order management

- **Wallet & Cashback System**
  - Digital wallet with balance tracking
  - Transaction history with pagination
  - Real-time balance updates
  - Transaction filtering by type and date range
  - Responsive wallet dashboard
  - Secure transaction processing

### Technical Stack
- **Frontend**: Next.js 13+ with App Router
- **Styling**: Tailwind CSS with Radix UI components
- **State Management**: React Query for data fetching and caching
- **Backend**: Supabase (PostgreSQL, Auth, Storage, Functions)
- **Type Safety**: TypeScript throughout the codebase

### Project Structure
```
HiyoRi-Ecommerce-Nextjs-Supabase/
├── src/
│   ├── app/
│   │   └── (store)/
│   │       └── wallet/          # Wallet page and related routes
│   │
│   ├── components/
│   │   └── wallet/             # Wallet-specific components
│   │       ├── WalletBalance.tsx
│   │       ├── TransactionList.tsx
│   │       ├── TransactionItem.tsx
│   │       ├── TransactionFilters.tsx
│   │       └── WalletSkeleton.tsx
│   │
│   ├── lib/
│   │   └── services/
│   │       └── walletService.ts # Wallet API and business logic
│   │
│   └── types/
│       └── wallet.ts           # Type definitions
│
└── supabase/
    └── migrations/             # Database migrations
        └── XXXX_wallet_tables.sql
```
## 2. Wallet Feature Details

### Data Models

#### Wallet
```typescript
interface Wallet {
  user_id: string
  balance: number
  currency: string
  updated_at: string
}
```
#### Wallet Transaction
```typescript
type TransactionType = 'cashback' | 'purchase' | 'refund'

interface WalletTransaction {
  id: string
  user_id: string
  amount: number
  type: TransactionType
  description: string
  reference_id?: string
  created_at: string
}
```
### Key Components

1. **Wallet Service**
   - Handles all wallet-related API calls
   - Manages transaction processing
   - Implements pagination and filtering
   - Handles error states and retries

2. **Wallet Page**
   - Displays current balance
   - Shows transaction history with load more
   - Filtering by transaction type and date range
   - Loading and error states
   - Responsive design

3. **Transaction Filters**
   - Type filtering (All/Credit/Debit)
   - Date range picker
   - Reset filters option

### Security Considerations
- All wallet operations require authentication
- Server-side validation of all transactions
- Rate limiting on wallet endpoints
- Audit logging for all balance changes
- Input sanitization for all user inputs

## 3. Development Workflow

### Setting Up
1. Clone the repository
2. Install dependencies: `pnpm install`
3. Set up environment variables (see `.env.example`)
4. Run development server: `pnpm dev`

### Testing
- Unit tests: `pnpm test`
- Integration tests: `pnpm test:integration`
- E2E tests: `pnpm test:e2e`

### Deployment
- Automatic deployments on `main` branch push
- Staging environment for testing
- Production deployments via GitHub releases
