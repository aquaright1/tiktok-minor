# TikTok Minor



## Pipeline Overview

1. Searches your keyword in the tiktok search bar 
2. Scrapes the top 10 profiles from the top 10 videos of the search
3. Aggregates the last 30 days of analytics (views, shares, likes, comments; 1 mil views in the last 30 days of posts)
4. Outputs to a dashboard to view/filter/sort/export the creators

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/tiktok-miner.git
cd tiktok-miner

# Install dependencies
bun install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with your configuration

# Initialize database
bun run db:migrate
bun run db:seed

# Start development server
bun run dev
```

Visit [http://localhost:3000](http://localhost:3000) to see the application.

### Docker Setup (Recommended)

```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

## 📋 Environment Configuration

Create a `.env.local` file with the following variables:

```bash
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/tiktok_miner"
REDIS_URL="redis://localhost:6379"

# External APIs
APIFY_API_TOKEN="your_apify_token"
OPENAI_API_KEY="your_openai_key"  # Optional for AI features

# Application
NEXT_PUBLIC_APP_URL="http://localhost:3000"
JWT_SECRET="your_secure_jwt_secret"

# Email (Optional)
SMTP_HOST="smtp.example.com"
SMTP_USER="your_email@domain.com"
SMTP_PASS="your_password"
```

## 📖 Usage Guide

### 1. Keyword Search
Navigate to the **Search** page and enter keywords, hashtags, or topics:
```
Examples:
- "fitness motivation"
- "#cooking"
- "tech reviews"
- "dance trends"
```


## 🗂 Project Structure

```
tiktok-miner/
├── app/                    # Next.js App Router
│   ├── page.tsx           # Dashboard homepage
│   ├── creators/          # Creator management pages
│   ├── scraper/          # Search & scraping interface
│   └── api/              # API routes
├── components/            # React components
│   ├── ui/               # Base UI components
│   ├── creators/         # Creator-specific components
│   └── charts/           # Data visualization
├── lib/                  # Core libraries
│   ├── db/               # Database utilities
│   ├── api/              # API clients
│   ├── scraper/          # Scraping services
│   └── analytics/        # Analytics engine
├── prisma/               # Database schema
├── docs/                 # Documentation
└── scripts/              # Utility scripts
```

## 🧪 Testing

```bash
# Run all tests
bun run test

# Run tests in watch mode
bun run test:watch

# Run integration tests
bun run test:integration

# Run E2E tests
bun run test:e2e

# Generate coverage report
bun run test:coverage
```

## 🚀 Deployment

### Development
```bash
bun run dev
```

### Production
```bash
bun run build
bun run start
```

### Docker
```bash
docker-compose -f docker-compose.prod.yml up -d
```
