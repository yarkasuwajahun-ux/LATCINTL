# WAKILIN ASKA - Pi Network Marketplace dApp

A complete, production-ready Pi Network marketplace dApp for selling fabrics, textiles, and clothing for men, women, children, and adults.

## 🚀 Features

- **Pi Network Integration**
  - Pi Authentication (Login with Pi)
  - Pi Payments (Testnet & Mainnet ready)
  - Secure payment processing with server approval

- **Product Catalog**
  - Fabrics & Textiles
  - Men's Clothing
  - Women's Clothing
  - Children's Clothing
  - Advanced search and filtering

- **E-Commerce Features**
  - Shopping cart management
  - Secure checkout process
  - Order history and tracking
  - User reviews and ratings
  - Payment history

- **Admin Dashboard**
  - Inventory management
  - Order management
  - User management
  - Sales analytics
  - Product management

- **Technical Stack**
  - Frontend: React + Tailwind CSS
  - Backend: Node.js with Express
  - Serverless: Vercel Functions
  - Authentication: Pi SDK
  - Payments: Pi Network SDK
  - Database: MongoDB (optional, with Firestore fallback)

## 📋 Project Structure

```
LATCINTL/
├── frontend/                 # React frontend application
│   ├── src/
│   │   ├── components/       # React components
│   │   ├── pages/           # Page components
│   │   ├── context/         # React Context (Auth, Cart, etc.)
│   │   ├── hooks/           # Custom hooks
│   │   ├── utils/           # Utility functions
│   │   ├── services/        # API services
│   │   ├── styles/          # CSS/Tailwind styles
│   │   └── App.jsx          # Main App component
│   ├── public/              # Static assets
│   ├── package.json
│   └── vite.config.js
├── backend/                  # Node.js backend
│   ├── api/                 # Vercel Serverless Functions
│   │   ├── auth.js          # Authentication endpoints
│   │   ├── payments.js      # Payment processing
│   │   ├── products.js      # Product management
│   │   ├── orders.js        # Order management
│   │   └── users.js         # User management
│   ├── lib/
│   │   ├── pi-sdk.js        # Pi SDK utilities
│   │   ├── database.js      # Database connection
│   │   └── security.js      # Security utilities
│   ├── middleware/          # Express middleware
│   ├── routes/              # Express routes
│   └── package.json
├── database/                 # Database schemas
│   ├── schemas/
│   │   ├── user.schema.js
│   │   ├── product.schema.js
│   │   ├── order.schema.js
│   │   └── payment.schema.js
│   └── seed-data.js
├── docs/                     # Documentation
│   ├── SETUP.md             # Setup guide
│   ├── API.md               # API documentation
│   ├── PI_INTEGRATION.md    # Pi Network integration guide
│   └── DEPLOYMENT.md        # Deployment guide
├── .env.example             # Environment variables example
├── .gitignore
├── vercel.json              # Vercel configuration
└── package.json             # Root package.json
```

## 🛠️ Setup Instructions

### Prerequisites
- Node.js 16+ and npm/yarn
- Vercel account for deployment
- Pi Network account and SDK access
- MongoDB or Firestore account (optional)

### 1. Clone and Install Dependencies

```bash
git clone https://github.com/yarkasuwajahun-ux/LATCINTL.git
cd LATCINTL

# Install root dependencies
npm install

# Install frontend dependencies
cd frontend && npm install && cd ..

# Install backend dependencies
cd backend && npm install && cd ..
```

### 2. Configure Environment Variables

Create `.env.local` files:

**`frontend/.env.local`**
```
VITE_API_URL=http://localhost:3001
VITE_PI_API_KEY=your_pi_api_key
VITE_PI_API_SECRET=your_pi_api_secret
VITE_PI_NETWORK=testnet  # or mainnet
```

**`backend/.env`**
```
NODE_ENV=development
PORT=3001
DATABASE_URL=your_database_url
PI_API_KEY=your_pi_api_key
PI_API_SECRET=your_pi_api_secret
PI_NETWORK=testnet
JWT_SECRET=your_jwt_secret
```

### 3. Start Development Servers

```bash
# Terminal 1 - Frontend
cd frontend && npm run dev

# Terminal 2 - Backend (Serverless locally)
cd backend && npx vercel dev
```

### 4. Deploy to Vercel

```bash
# Deploy frontend
cd frontend
vercel

# Deploy backend (Serverless Functions)
cd ../backend
vercel
```

## 💳 Pi Network Payment Flow

### Payment Processing Steps

1. **Create Payment** (`createPayment`)
   ```javascript
   const payment = await piPayment.createPayment({
     amount: productPrice,
     memo: "Purchase LATCINTL items",
     metadata: { orderId, userId }
   });
   ```

2. **Server Approval** (`/api/payments/approve`)
   ```javascript
   const approval = await fetch('/api/payments/approve', {
     method: 'POST',
     body: JSON.stringify({ paymentId, userId })
   });
   ```

3. **Complete Payment** (`completePayment`)
   ```javascript
   const completed = await piPayment.completePayment(paymentId, txid);
   ```

## 📚 API Endpoints

### Authentication
- `POST /api/auth/login` - Login with Pi
- `POST /api/auth/logout` - Logout
- `GET /api/auth/user` - Get current user

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get single product
- `POST /api/products` - Create product (Admin)
- `PUT /api/products/:id` - Update product (Admin)
- `DELETE /api/products/:id` - Delete product (Admin)

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders/:id` - Get order details
- `GET /api/orders` - Get user's orders
- `PUT /api/orders/:id` - Update order status (Admin)

### Payments
- `POST /api/payments/create` - Create payment
- `POST /api/payments/approve` - Server-side approval
- `POST /api/payments/complete` - Complete payment
- `GET /api/payments/:id` - Get payment status

## 🔐 Security Features

- ✅ Pi Network SDK integration for secure authentication
- ✅ JWT token-based sessions
- ✅ Server-side payment approval
- ✅ Input validation and sanitization
- ✅ CORS protection
- ✅ Rate limiting
- ✅ Environment variable protection

## 📱 Pi Browser Compatibility

- Responsive design optimized for mobile
- Pi App Studio compatible
- Webview-optimized performance
- Touch-friendly UI/UX
- Minimal external dependencies

## 🚀 Production Deployment

### Vercel Deployment

1. Push code to GitHub
2. Connect repository to Vercel
3. Set environment variables in Vercel dashboard
4. Deploy automatically on push

### Environment Setup

```bash
# Testnet (for development)
VITE_PI_NETWORK=testnet

# Mainnet (for production)
VITE_PI_NETWORK=mainnet
```

## 📖 Documentation

- [Setup Guide](./docs/SETUP.md) - Detailed setup instructions
- [API Documentation](./docs/API.md) - API endpoints and examples
- [Pi Integration Guide](./docs/PI_INTEGRATION.md) - Pi Network integration details
- [Deployment Guide](./docs/DEPLOYMENT.md) - Production deployment guide

## 🤝 Support & Resources

- [Pi Network Developer Docs](https://docs.pi-network.dev)
- [Pi SDK Documentation](https://docs.pi-network.dev/SDK)
- [Vercel Documentation](https://vercel.com/docs)

## 📝 License

MIT License - See LICENSE file for details

## 🙌 Contributing

Contributions are welcome! Please read our contributing guidelines before submitting PRs.

---

**Made with ❤️ for the Pi Network Community**
