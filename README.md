# schwab-trader

Project Overview: 
Creating a personal automated investment application that replicates some functionality of robo-advisors (like Wealthfront) but with direct ownership of shares through a Schwab account. 
The key difference from traditional robo-advisors is that this system will work with whole shares only (no fractional shares) and will directly own shares in your personal account rather than through a managed account structure. 

Core Requirements (subject to change): 
  1. Portfolio Management - Allow configuration of target portfolio allocations across multiple ETFs - Support multiple independent portfolios - Track only purchases made through the automation (ignore existing holdings) - Have "cash on hand" tracked independently between portfolios and pre-existing cash - Handle variable deposit amounts (weekly, monthly, etc.) - Handle deposits of any size - Manage portfolio without fractional shares - Deploy cash opportunistically to maintain target allocations
  3. Trading Integration - Interface with Schwab's API for: - Real-time market data via WebSocket connection - Account balance monitoring - Trade execution - Handle limit orders with retry logic - Manage whole-share purchases only
  4. Portfolio Tracking & Analytics - Independent portfolio tracking separate from existing holdings - Performance monitoring - Transaction history - Portfolio allocation visualization - Basic observability and reporting
  
  
Technical Architecture: 
  1. Frontend: - React-based web application - TypeScript for type safety - Modern UI components for portfolio management - Real-time updates via WebSocket - Data visualization for portfolio analytics
  2. Backend: - Node.js/Express server - MongoDB database (as used in fullstackopen) - Integration with Schwab's APIs: - REST API for account/trading - WebSocket API for market data
  3. AWS Integration: - Potential use of native AWS services for: - Hosting - Scheduled tasks (Lambda) - Event processing - Analytics (QuickSight)

Learning Goals: - Develop React/JavaScript skills in parallel with fullstackopen course - Build a practical, production-ready application - Learn full-stack development practices - Gain experience with financial APIs and real-time data
