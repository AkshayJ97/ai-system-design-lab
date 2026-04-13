# Requirements Template
- **Swiggy** : Create a document stating functional and non-functional requirement for food-delivery app like swiggy.
## Users

### Primary Users
- **Customers**: Users who search for restaurants, browse menus, place orders, and track deliveries
- **Restaurant Owners**: Business owners who manage menus, inventory, pricing, and promotional offers
- **Support Staff**: Internal team handling customer service and dispute resolution

---

## Functional Requirements

### Customer Features
- [ ] Search restaurants and food items with filters (cuisine, rating, delivery time, price range)
- [ ] Filter by dietary preferences, delivery options, and availability
- [ ] View restaurant details, menus, reviews, and ratings
- [ ] Add items to cart with customizations (size, toppings, special instructions)
- [ ] Place orders with address selection and scheduling
- [ ] Pay using multiple methods (credit/debit cards, digital wallets, UPI, cash on delivery)
- [ ] Track order status in real-time with live location updates
- [ ] View order history with ability to reorder
- [ ] Rate and review orders
- [ ] Manage favorites and saved addresses
- [ ] Receive order notifications (confirmation, preparation, dispatch, delivery)

### Restaurant Owner Features
- [ ] Manage menu items (add, edit, delete, categorize)
- [ ] Update item availability and stock levels
- [ ] Set and manage pricing and discounts
- [ ] Create and manage promotional offers and campaigns
- [ ] View incoming orders and order queue
- [ ] Mark order status (received, preparing, ready, dispatched)
- [ ] Manage restaurant operating hours
- [ ] View analytics and sales reports
- [ ] Manage restaurant profile and photos

---

## Non-Functional Requirements

### Performance
- **Throughput**: System should handle up to **100,000 orders per second** under peak load
- **Latency**: 95th percentile latency should not exceed **500 ms** during peak time
- **Response Time**: API responses should complete within **200 ms** for 99% of requests
- **Search Performance**: Restaurant search results should load within **300 ms**
- **Real-time Updates**: Order status updates should propagate within **2 seconds**

### Availability & Reliability
- **Uptime**: System should maintain **99.9% availability** (allow ~43 minutes downtime/month)
- **Disaster Recovery**: RPO (Recovery Point Objective): **1 minute** | RTO (Recovery Time Objective): **5 minutes**
- **Data Durability**: Replicate data across **3 availability zones**
- **Graceful Degradation**: Non-critical features should degrade rather than cause total failure

### Security
- **Data Encryption**: All sensitive data (passwords, payment info, PII) encrypted **at rest** (AES-256)
- **Transit Security**: All communications use **TLS 1.3**
- **Authentication**: Multi-factor authentication for sensitive operations
- **Payment Security**: PCI-DSS Level 1 compliance; never store full card details
- **Rate Limiting**: Implement rate limiting to prevent abuse (API: 1000 req/min per user)
- **Authorization**: Role-based access control (RBAC) for all operations

### Observability
- **Centralized Logging**: All application and system logs aggregated in single location
- **Monitoring**: Real-time dashboards monitoring key metrics (latency, error rate, throughput)
- **Alerting**: Automated alerts for critical issues (uptime < 99.9%, error rate > 1%, latency > 500ms)
- **Tracing**: Distributed tracing for end-to-end request tracking
- **Metrics**: Track application, infrastructure, and business metrics

### Scalability
- **Horizontal Scaling**: Architecture supports adding more servers dynamically
- **Data Scaling**: Database should handle growth to **100 million users**
- **Storage**: Support petabyte-scale data storage with efficient retrieval
- **Cache**: Implement multi-level caching (in-memory, distributed cache) with 95%+ hit rate

### Maintainability
- **Code Quality**: Maintain code coverage > 80%
- **Documentation**: Keep API documentation and system design docs up-to-date
- **Deployment**: Support zero-downtime deployments
- **Rollback**: Ability to rollback failed deployments within **5 minutes**

---

## Out of Scope

- [ ] Integration with external delivery partners (initially in-house delivery only)
- [ ] Meal planning and nutritional recommendations
- [ ] Social features (user following, sharing, recommendations based on friends)
- [ ] Restaurant booking/reservations for dine-in
- [ ] Subscription or loyalty program features (v1)
- [ ] AI-based demand forecasting and menu optimization
- [ ] Multi-language support (English only for v1)
- [ ] Accessibility features (WCAG compliance) - scheduled for v2

---

## Constraints

### Technical Constraints
- Must be cloud-agnostic (not locked into single cloud provider)
- Use open-source technologies where possible to reduce licensing costs
- Support both iOS and Android apps (no web for v1)
- API-first architecture for flexibility

### Business Constraints
- Budget limited to **$500K** for infrastructure in first year
- Team size: **15 engineers** maximum
- Must launch in **6 months**
- Target market: **single metropolitan area** initially

### Regulatory Constraints
- Comply with local food safety regulations
- Must handle consumer data according to local privacy laws
- Payment processing must comply with financial regulations
- Tax compliance for restaurant transactions

---

## Dependencies & Assumptions

### Key Assumptions
- Average order value: **250Rs.**
- Peak traffic: **10x average traffic**
- 70% of users will use mobile app
- Average order processing time: **30 minutes**
- Data retention: **7 years** for transaction logs, **1 year** for user activity logs

### External Dependencies
- Payment gateway provider (Stripe/Razorpay)
- SMS/Email service for notifications
- Cloud infrastructure provider (AWS/GCP/Azure)
- Maps API for location services

---

## Success Metrics

- [ ] System meets 99.9% uptime SLA in production
- [ ] 95th percentile latency stays below 500ms during peak hours
- [ ] Customer satisfaction score > 4.5/5
- [ ] Order placement success rate > 99.5%
- [ ] Payment success rate > 99.8%
- [ ] System cost per order < $0.50
 