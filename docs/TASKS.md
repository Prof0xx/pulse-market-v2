# pulse-market — Task Queue

> Each task is a unit of work for one Cursor agent session.
> Work top-to-bottom. Do not skip. Do not reorder.
> Mark `[x]` when verify passes. Add a completion note.
>
> **Done definition:** A task is only complete when its Verify commands pass AND this file is updated with `[x]` and a 1-2 line note. No exceptions.

## - [ ] T1 Project Setup & Environment

**Creative Vision:** Modern Next.js 14 development environment with premium tooling, zero-config setup, and developer experience that feels effortless.

**Scope:** Initialize Next.js 14 project with TypeScript, install all production dependencies, configure development tools, and establish proper folder structure for a gaming-aesthetic prediction market.

**Implementation Details:**
- Use `create-next-app@latest` with TypeScript and App Router
- Install core dependencies: `framer-motion zustand @trpc/client @trpc/server @prisma/client prisma tailwindcss @tailwindcss/typography`
- Install UI dependencies: `@radix-ui/react-dialog @radix-ui/react-dropdown-menu @radix-ui/react-select lucide-react`
- Configure TypeScript with strict mode, ESLint with Next.js config, Prettier
- Set up folder structure: `src/app`, `src/components/ui`, `src/lib`, `src/styles`

**AC:**
- [ ] Next.js 14 app created with App Router and TypeScript
- [ ] All dependencies installed and versions compatible
- [ ] Development server starts at localhost:3000 without errors
- [ ] TypeScript compiles with strict mode enabled
- [ ] ESLint runs without errors, Prettier formats code correctly
- [ ] Folder structure matches modern Next.js 14 patterns

**Verify:**
```bash
npm run dev
npm run type-check
npm run lint
npm run build
curl -f http://localhost:3000
```

---

## - [ ] T2 Design System & Tailwind Configuration

**Creative Vision:** Neon-dark gaming aesthetic with electric green/blue gradients, custom animations, and data visualization components that make users feel like professional traders in a futuristic environment.

**Scope:** Implement complete design system with custom Tailwind configuration, color palette, typography, and base UI components that match the gaming-meets-trading aesthetic.

**Implementation Details:**
- Configure `tailwind.config.js` with custom colors: electric-green (#00ff88), electric-blue (#00ccff), dark backgrounds
- Add custom font stack: JetBrains Mono for data, Inter for UI text
- Create design tokens for spacing, shadows, animations, gradients
- Implement base UI components: Button, Input, Card, Badge with neon styling
- Add custom CSS for glow effects, gradients, and premium shadows

**AC:**
- [ ] Tailwind config includes all custom colors and design tokens
- [ ] Typography system works with monospace for numbers, sans-serif for text
- [ ] Base UI components render with neon-dark styling and gradients
- [ ] Hover effects and glow animations working smoothly
- [ ] Responsive design system works across mobile, tablet, desktop

**Verify:**
```bash
npm run dev
npm run build
# Visual check: All components have neon styling with gradients
# Test responsiveness: Components adapt to different screen sizes
```

---

## - [ ] T3 Database Schema & Prisma Setup

**Creative Vision:** Production-ready database architecture that supports rapid 10-minute prediction cycles, real-time betting, social features, and scalable performance under high load.

**Scope:** Implement complete Prisma schema with all models for users, events, bets, outcomes, social features, and real-time data with proper relationships and performance indexes.

**Implementation Details:**
- Create `prisma/schema.prisma` with User, Event, Outcome, Bet, Comment, Reaction, Achievement models
- Add proper relationships: User -> Bets, Event -> Outcomes, User -> Achievements
- Include performance indexes on frequently queried fields (userId, eventId, createdAt)
- Add validation constraints and default values for all fields
- Create seed script with sample prediction events and users

**AC:**
- [ ] Prisma schema includes all models with correct field types and relationships
- [ ] Database migrations run successfully without errors
- [ ] Prisma client generates and typings are correct
- [ ] Seed script populates database with realistic sample data
- [ ] Prisma Studio opens and shows all models with data

**Verify:**
```bash
npx prisma migrate dev --name init
npx prisma generate
npx prisma db seed
npx prisma studio
# Check: All models visible with relationships working
```

---

## - [ ] T4 tRPC API Layer & Real-time Features

**Creative Vision:** Type-safe API layer with real-time odds updates, instant bet placement, and WebSocket subscriptions that make the app feel live and responsive like a professional trading platform.

**Scope:** Implement complete tRPC router with all endpoints for authentication, events, betting, social features, plus real-time subscriptions for odds updates and live data.

**Implementation Details:**
- Set up tRPC server in `src/server/api/root.ts` with proper TypeScript integration
- Create routers: `auth.ts`, `events.ts`, `betting.ts`, `social.ts` with full CRUD operations
- Add Zod validation schemas for all inputs with comprehensive error handling
- Implement real-time subscriptions for odds updates using WebSockets
- Add middleware for authentication, rate limiting, and error handling

**AC:**
- [ ] tRPC server configured and all endpoints working
- [ ] All routers have proper Zod validation and TypeScript types
- [ ] Real-time subscriptions working for odds updates
- [ ] Authentication middleware properly protecting endpoints
- [ ] Error handling returns consistent error messages with proper HTTP codes
- [ ] Client-server type safety working end-to-end

**Verify:**
```bash
npm run dev
curl -X POST http://localhost:3000/api/trpc/events.list
npm run type-check
# Test: API endpoints return expected data structure
# Test: Real-time subscriptions push updates to connected clients
```

---

## - [ ] T5 Core Prediction Market Features

**Creative Vision:** Innovative prediction market interface with visual odds charts, one-click betting, streak tracking, and social leaderboards that make betting feel like gaming with instant gratification.

**Scope:** Build main prediction market features: event discovery, bet placement, odds visualization, user profiles, and social features with smooth animations and premium UX.

**Implementation Details:**
- Create EventCard component with real-time odds, countdown timers, and bet buttons
- Implement BetSlider with haptic feedback, payout calculation, and success animations
- Add EventDetails page with full bet history, comments, and social sharing
- Create Profile page with bet history, achievements, leaderboards, and stats
- Implement real-time updates with optimistic UI and error recovery

**AC:**
- [ ] Event discovery page shows active events with real-time odds updates
- [ ] Bet placement works end-to-end with proper validation and confirmation
- [ ] Odds visualization updates in real-time and shows price movements
- [ ] User profiles show comprehensive stats, achievements, and history
- [ ] Social features (comments, reactions, leaderboards) working smoothly
- [ ] Mobile experience feels native with touch interactions and gestures

**Verify:**
```bash
npm run dev
npm run test:e2e:betting-flow
npm run test:e2e:social-features
npm run lighthouse:mobile
# Test: Full betting flow from event discovery to payout works
# Test: Social features and real-time updates functioning
```

---

## - [ ] T6 Premium Animations & Micro-interactions

**Creative Vision:** Gaming-quality animations with spring physics, particle effects, success celebrations, and micro-interactions that make every action feel premium and satisfying.

**Scope:** Implement comprehensive animation system with Framer Motion, including page transitions, bet placement animations, success states, loading animations, and mobile gestures.

**Implementation Details:**
- Add page transitions with smooth enter/exit animations
- Create bet placement flow with confirmation, loading, and success particle effects
- Implement micro-interactions: button hovers, card lifts, number counting animations
- Add mobile gesture support: swipe to bet, pull to refresh, tap feedback
- Optimize all animations for 60fps performance with GPU acceleration

**AC:**
- [ ] All page transitions smooth and contextually appropriate
- [ ] Bet placement has satisfying animation sequence with success celebration
- [ ] Micro-interactions provide clear feedback for every user action
- [ ] Mobile gestures feel natural and responsive
- [ ] All animations maintain 60fps on mobile devices
- [ ] Loading states keep users engaged with skeleton UI and progress indicators

**Verify:**
```bash
npm run dev
npm run test:animations:performance
npm run lighthouse:performance
# Visual test: All animations smooth and purposeful
# Performance test: Animations maintain 60fps in Chrome DevTools
```

---

## - [ ] T7 Comprehensive Testing & Quality Assurance

**Creative Vision:** Production-grade testing suite that ensures reliability, prevents regressions, and maintains code quality at startup levels with automated quality gates.

**Scope:** Implement complete testing strategy with unit tests, integration tests, end-to-end tests, accessibility testing, and performance validation.

**Implementation Details:**
- Set up Vitest for unit testing with coverage reporting
- Add React Testing Library for component testing
- Implement Playwright for end-to-end testing across browsers
- Add accessibility testing with axe-core integration
- Set up performance testing with Lighthouse CI

**AC:**
- [ ] Unit test coverage >80% for business logic and utilities
- [ ] Integration tests cover all tRPC endpoints and database operations
- [ ] E2E tests validate critical user journeys (signup, bet, payout)
- [ ] Accessibility tests pass WCAG 2.1 AA standards
- [ ] Performance tests achieve >90 Lighthouse scores on mobile and desktop
- [ ] All tests run in CI/CD pipeline with proper failure handling

**Verify:**
```bash
npm run test:unit
npm run test:integration
npm run test:e2e
npm run test:accessibility
npm run lighthouse:ci
npm run test:coverage
# All test suites pass with coverage targets met
```

---

## - [ ] T8 Production Deployment & Monitoring

**Creative Vision:** Production deployment with zero-downtime capability, comprehensive monitoring, error tracking, and performance analytics that enable rapid iteration and scaling.

**Scope:** Deploy application to production with complete CI/CD pipeline, monitoring, error tracking, analytics, and performance optimization.

**Implementation Details:**
- Set up GitHub Actions CI/CD pipeline with automated testing and deployment
- Deploy to Vercel with custom domain and SSL certificates
- Configure Sentry for error tracking and performance monitoring
- Add Vercel Analytics for user behavior and performance metrics
- Set up database backups and monitoring alerts

**AC:**
- [ ] Application deployed to production with custom domain and SSL
- [ ] CI/CD pipeline automatically deploys on merge to main branch
- [ ] Error tracking captures and reports all production errors
- [ ] Performance monitoring tracks Core Web Vitals and API response times
- [ ] Database backups running automatically with tested restore procedures
- [ ] Health checks and uptime monitoring configured with alerting

**Verify:**
```bash
npm run deploy:production
npm run health-check:production
curl -f https://your-domain.com/api/health
npm run lighthouse:production
# Production site accessible and performant
# Monitoring systems receiving data and alerts configured
```

---

Generated by Prof's AI Council V2 — AI-executable tasks with creative vision and production quality.