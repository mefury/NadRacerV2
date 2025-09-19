# NadRacer 🚀

A fullstack 3D space racing game with blockchain integration, featuring immersive WebGL graphics and competitive leaderboards.

## 🎮 Overview

NadRacer is an exciting 3D space racing game built with modern web technologies. Race through space, compete with other players, and climb the leaderboards with blockchain-verified scores.

### Features

- **3D Graphics**: Immersive WebGL-powered racing experience using Three.js
- **Blockchain Integration**: Secure leaderboard system with Monad blockchain
- **Authentication**: Privy-powered Web3 authentication
- **Real-time Competition**: Live leaderboards and scoring
- **Modern UI**: Beautiful interface built with React and Tailwind CSS

## 🏗️ Project Structure

```
NadRacer/
├── client/          # React frontend with Three.js
├── server/          # Node.js/Express backend
├── .gitignore       # Git ignore patterns
└── README.md        # This file
```

## 🚀 Quick Start

### Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/mefury/NadRacerV2.git
   cd NadRacerV2
   ```

2. **Install dependencies**
   ```bash
   # Install client dependencies
   cd client
   npm install

   # Install server dependencies
   cd ../server
   npm install
   ```

3. **Environment Setup**
   ```bash
   # In the server directory, create a .env file
   cd server
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Development**
   ```bash
   # Terminal 1: Start the server
   cd server
   npm run dev

   # Terminal 2: Start the client
   cd client
   npm run dev
   ```

5. **Open your browser**
   - Client: http://localhost:5173
   - Server API: http://localhost:3001

## 📁 Client

The client is a modern React application built with:

- **React 19** - Latest React features
- **Vite** - Lightning-fast build tool
- **Three.js** - 3D graphics and WebGL
- **OGL** - Lightweight WebGL library
- **Tailwind CSS** - Utility-first CSS framework
- **Privy** - Web3 authentication
- **Framer Motion** - Smooth animations

### Client Commands

```bash
cd client
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
npm test        # Run tests
```

## 🖥️ Server

The server is a Node.js/Express API with:

- **Express** - Web framework
- **Viem** - Ethereum library for blockchain integration
- **CORS** - Cross-origin resource sharing
- **Helmet** - Security middleware
- **Rate Limiting** - API protection

### Server Commands

```bash
cd server
npm start       # Start production server
npm run dev     # Start development server with nodemon
```

## 🛠️ Development

### Running Both Services

For convenience, you can run both client and server simultaneously:

```bash
# Terminal 1
cd server && npm run dev

# Terminal 2  
cd client && npm run dev
```

### Building for Production

```bash
# Build client
cd client
npm run build

# The server runs in production mode with:
cd server
npm start
```

## 🚀 Deployment

### Client Deployment
The client builds to a `dist/` folder ready for deployment to:
- Vercel
- Netlify
- GitHub Pages
- Any static hosting service

### Server Deployment
The server can be deployed to:
- Railway
- Render
- Heroku
- DigitalOcean
- AWS/GCP/Azure

## 🔒 Environment Variables

### Server (.env)
```
PORT=3001
NODE_ENV=development
# Add your blockchain/database configurations here
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under UNLICENSED - see the package.json files for details.

## 👨‍💻 Author

**MEFURY**

## 🎯 Roadmap

- [ ] Multiplayer racing
- [ ] More spacecraft types
- [ ] Custom race tracks
- [ ] Tournament system
- [ ] NFT integration
- [ ] Mobile app

---

**Happy Racing! 🏁**