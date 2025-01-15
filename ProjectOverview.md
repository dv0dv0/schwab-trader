# Trading Application - Project Overview

## 1. Project Description
This project is a personal trading application built to interface with the Charles Schwab Trader API. 

This is a personal automated investment application that replicates some functionality of robo-advisors (like Wealthfront) but with direct ownership of shares through a Schwab account. The key difference from traditional robo-advisors is that this system will work with whole shares only (no fractional shares) and will directly own shares in your personal account rather than through a managed account structure. A key feature of this will be that it will accept investments of any dollar amount.  With clever purchasing logic, the app should be able to look at the desired weighted components of a user's desired portfolio composition, and purchase shares based on available funds and the purchase price of those shares.  The user should be able to modify the portfolio composition, and at this time the rebalancing should only be achieved with purchasing.  There should be no selling at this stage, maybe in the future.

The development process is intended to be complimentary or in parallel with the Full Stack Open (FSO) course curriculum, emphasizing learning and understanding over rapid development. Each component will be thoroughly tested and documented, ensuring complete comprehension of all implemented features.  I would like to minimize copying large amounts of code, and I don't want to have any code at all that I don't fully understand. The development approach prioritizes building small, modular, well-understood modules that gradually integrate into a comprehensive trading platform. 

The application will be initially developed for personal use, with an eventual, potential future expansion for broader user bases (this is low priority). Another key differentiatior between this and other robo-advisors is that a future potential monetization would be a flat-rate/monthly, not a percentage of managed funds, which will be much cheaper for customers.

Because this is a finance related application, the security posture and controls need to be tight.  I want to make sure that only the absolutely necessary API calls to the Schwab API are being made, and that there are guards against costly errors.

This will be a client-server type application with strict separation of concerns for security. The frontend client will only handle user interface operations like portfolio configuration and monitoring. All sensitive operations, including API authentication and trading execution, will be handled exclusively by the backend server. The frontend will communicate with our backend server via a REST API, never directly with the Schwab API. This ensures that sensitive credentials and API keys remain secure on the server side. The backend will also be managing the portfolio/user/trade data as well as performing trades automatically based on how the portfolios are configured, and any other supporting functions.  This app does not intend to compete with or replace a typical trading platform, there may need to be basic market visualization capabilities, purely to be able to track portfolio performance against other investing options, but the data does not need to be very granular/realtime, I would expect users to utilize other tools for that.  I want to be wary of Schwab API rate limits and want to be efficient as possible.



## 2. Objectives

### Application Objectives
- Create a functional trading platform interfacing with the Schwab API
- Create logic to choose which shares to purchase to move portfolio towards target composition
- Implement basic market data visualization - does not need to be very granular 
- Provide multi-portfolio tracking and management capabilities
- Implement configurable cash management accross multiple portfolios
- Enable order placement and management
- Establish robust error handling for trading operations
- Monitor account activity effectively
- Employ security best practices
- Define and manage investment rules and strategies
- Implement automated trading schedules
- Support multiple portfolio strategies/templates
- Provide audit trails for automated decisions
- Calculate and execute optimal trade sizing
- Build a data foundation on which to eventually perform analytics and potentially analyze with AI tools

### Learning Objectives
- Gain practical experience with React development
- Learn best practices for API integration
- Develop skills in test-driven development
- Master state management in React applications
- Build expertise in WebSocket implementation
- Understand OAuth authentication flows

## 3. Target Users
Initial development focuses on a single user profile:
- Individual trader (self)
- Requires real-time market data access
- Accepts any dollar amount of investment, even if its smaller than the price of the cheapest share in the portfolio
- Needs portfolio tracking capabilities
- Values thorough understanding of the trading platform's functionality

Future expansion may consider (low priority):
- Other individual traders
- Small trading groups
- Potential for commercial applications

## 4. Key Features
- Real-time market data visualization
  - Stock price displays
  - Basic technical charts (this will not replace or compete with a typical trading platform - purely for portfolio tracking/comparison)
  - Market indicators
  
- Portfolio Management
  - Holdings overview
  - Performance tracking
  - Position monitoring
  - Automated purchasing logic
  
- Cash management
  - Cash allocation across portfolios
  - Cash reserve management
  - Investment scheduling

- Order Management
  - Order placement
  - Failed order handling
  - Order tracking
  - Order modification
  
- Account Activity Monitoring
  - Transaction history
  - Account balance tracking
  - Position updates

- Error handling & recovery
  - Failed trade management
  - System status monitoring
  - Automated error recovery

- Analytics Tools
  - Basic technical analysis
  - Portfolio performance metrics
  - Risk assessment tools

- Automation
  - Portfolio rebalancing logic
  - Trade scheduling system
  - Investment rules engine
  - Trade verification workflow
  - Audit logging of automated decisions
  - Dollar-cost averaging capabilities

## 5. Technology Stack
- Frontend Framework: React
- Backend: Node.js/Express
- Testing: Jest and React Testing Library
- API Integration: Schwab Trader API
- API Documentation: TBD
- Job scheduling: TBD
- Real-time Data: WebSocket connections
- Database: MongoDB
- Authentication: OAuth 2.0
- Development Tools:
  - VS Code
  - Git/GitHub
  - Chrome DevTools

## 6. Development Principles
- Test-Driven Development
  - Write tests before implementation
  - Maintain high test coverage
  - Focus on component isolation

- Documentation Requirements
  - Thorough component documentation
  - API integration details
  - Setup and configuration guides
  - Code comments and explanations

- Learning-Focused Process
  - Align with FSO course progression
  - Build small, focused modules
  - Ensure complete understanding before progression
  - Regular code reviews and refactoring

- Code Quality Standards
  - Follow React best practices
  - Maintain consistent coding style
  - Regular refactoring sessions
  - Peer review process (future)

- Other
  - Error handling strategy
  - Logging standards
  - Performance benchmarks
  - Backup/recovery procedures

## 7. Project Constraints
- Technical Limitations
  - Schwab API restrictions and rate limits
  - WebSocket connection limitations
  - Browser performance considerations
  - Data storage/retention requirements
  - System availability requirements

- Usage Limitations
  - Portfolio rebalancing frequency limitations
  - Minimum trade size requirements (should be able to handle any amount of capital)
  - Account balance requirements (need to have enough cash to complete each trade)
  - Trading hours limitations
  - Multi-portfolio management complexity (this involves managing/allocating cash inflows)
  - Error tolerance thresholds
  - Cash management constraints


- Development Timeline
  - Either:
        Paced with FSO course progression
        or
        Backend to Frontend path, creating backend modules to eventually be utilized by the frontend
  - Focus on learning over rapid development
  - Flexible milestone scheduling

- Learning Considerations
  - New concept introduction rate
  - Technology learning curve
  - Testing methodology learning
  - API integration complexity

## 8. Security & Risk Management

### Architecture Security
- Complete separation of sensitive operations
  - All Schwab API interactions handled server-side only
  - API keys and credentials never exposed to client
  - Frontend restricted to authenticated REST API calls to backend
  - Backend validates all frontend requests before executing trades

### Security Approach
- Principle of Least Privilege
  - Minimal necessary Schwab API permissions
  - Limited access to trading functionality
  - Strict API request validation

### Risk Controls
- Configurable Trading Limits
  - Configurable maximum single trade amount
  - Configurable daily trading limits
  - Configurable portfolio allocation limits
  - Configurable thresholds for human verification
  - All limits stored and enforced server-side

### Authentication & Authorization
- Secure credential storage
- Multi-factor authentication for high-risk operations
- Session management
- API token security

### Monitoring & Alerts
- Automated notification system
  - Large trade alerts
  - Error notifications
  - System status updates
- Activity logging
  - All trading activity
  - System access logs
  - Error logs

### Data Security
- Encrypted storage of sensitive data
- Secure API communication
- Regular security audits
- Backup procedures
