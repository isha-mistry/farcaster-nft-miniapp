# Farcaster + Arbitrum Mini-App Starter

<p align="center">
  <a href="https://github.com/your-org/your-repo/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT" />
  </a>
  <a href="https://vitejs.dev/">
    <img src="https://img.shields.io/badge/Built%20with-Vite-646CFF.svg?logo=vite&logoColor=white" alt="Vite" />
  </a>
  <a href="https://react.dev/">
    <img src="https://img.shields.io/badge/Frontend-React-61DAFB.svg?logo=react&logoColor=white" alt="React" />
  </a>
  <a href="https://arbitrum.io/stylus">
    <img src="https://img.shields.io/badge/Arbitrum-Stylus-28A0F0.svg?logo=arbitrum&logoColor=white" alt="Arbitrum Stylus" />
  </a>
</p>

A modern, full-stack starter template for building your own [Farcaster Mini-App](https://docs.farcaster.xyz/) with [Arbitrum Stylus](https://arbitrum.io/stylus) smart contracts, TypeScript React frontend, and seamless wallet/NFT integration.

## ✨ Features

- **Minimal, production-ready React (Vite + Tailwind) frontend**
- **Wallet connection** (wagmi + viem) with support for Farcaster Frame and browser wallets
- **Arbitrum Stylus NFT contract** (Rust, OpenZeppelin crate, ERC721)
- **Event-based NFT discovery** (no need for full ERC721 ABI)
- **Easy contract ABI/address injection**
- **Farcaster manifest and frame meta integration**
- **Simple UI:** Connect wallet, mint NFT, view NFT gallery, share to Farcaster

## ⚡ Quick Start

```bash
# 1. Clone this template
git clone https://github.com/hummusonrails/farcaster-arb-miniapp-starter.git
cd farcaster-arb-miniapp-starter

# 2. Install dependencies
npm install

# 3. Run the frontend locally
npm run dev
```

### Contract (Rust, Stylus)

First, make sure Rust and Stylus tooling are installed. Follow the instructions in the [Stylus QuickStart Guide](https://docs.arbitrum.io/stylus/quickstart#setting-up-your-development-environment).

```bash
# 4. Build and deploy your contract
cd contracts/template
cargo stylus deploy \
  --endpoint='http://localhost:8547' \
  --private-key="0xb6b15c8cb491557369f3c7d2c287b053eb229daa9c22138887752191c9520659"

# 5. Update the contract address in src/App.tsx
CONTRACT_ADDRESS = "PUT_YOUR_CONTRACT_ADDRESS_HERE"
```

## 🛠️ How to Use This Template

### 1. **Customize and Deploy Your Stylus Contract**

- Edit `contracts/template/src/lib.rs` for your NFT or app logic (uses OpenZeppelin ERC721).
- Build and deploy to Arbitrum local devnode, or Arbitrum's testnet/mainnet.
- Export your contract’s ABI (see below).

### 2. **Update the Frontend**

- Place your contract ABI in `src/abi/SampleNFT.json`.
- Update the contract address in `src/App.tsx` (`CONTRACT_ADDRESS`).
- Customize UI in `src/App.tsx` and other components as needed.

### 3. **Farcaster Integration**

- Edit `public/.well-known/farcaster.json` to describe your miniapp.
- Add your production URL to `<meta name="fc:frame">` in `public/index.html`.
- See [Farcaster Mini-App docs](https://docs.farcaster.xyz/developers/mini-apps/overview) for manifest and frame embed requirements.

## 🧩 File Structure

```
farcaster-arb-miniapp-starter/
├── contracts/           # Stylus (Rust) smart contracts
│   └── template/
│       ├── src/lib.rs   # NFT contract logic (ERC721)
│       └── README.md
├── public/              # Static assets, Farcaster manifest, NFT images
│   └── .well-known/farcaster.json
├── src/
│   ├── abi/             # Contract ABIs (JSON)
│   ├── App.tsx          # Main React app
│   ├── wagmi.ts         # Wagmi config (chains, connectors)
│   ├── hooks/
│   │   └── usePublicClient.ts # viem public client
│   └── viemChains.ts    # Chain definitions (Nitro localhost, Arbitrum, Sepolia)
├── package.json
├── README.md
└── ...
```

## 🧑‍💻 Developer Guide

### ✍️ Contract Development

- Write your Stylus contract in Rust.
- Export the ABI after building:
  ```bash
  cargo stylus export-abi --json
  ```
- Copy the ABI to `src/abi/SampleNFT.json`.

### ⚛️ Frontend Customization

- Change branding, app name, and icons in `public/` and inside `src/`.
- Add or remove UI components in `src/App.tsx`.

### 🔗 Farcaster & Wallet

- Supports both browser wallets and Farcaster Frame connector.
- Add your app to Farcaster via the manifest and meta tags.

## Resources

- [Farcaster Mini-Apps](https://docs.farcaster.xyz/developers/mini-apps/overview)
- [Arbitrum Stylus](https://arbitrum.io/stylus)
- [OpenZeppelin Stylus](https://github.com/OpenZeppelin/openzeppelin-stylus)
- [wagmi](https://wagmi.sh/)
- [viem](https://viem.sh/)
- [Vite](https://vitejs.dev/)
- [Tailwind CSS](https://tailwindcss.com/)

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙋‍♂️ FAQ

**Q: Can I use this for non-NFT contracts?**  
A: Yes! The contract provided is only a template. You can modify it to suit your needs.

**Q: How do I update the contract ABI/address?**  
A: Replace `src/abi/SampleNFT.json` and update `CONTRACT_ADDRESS` in `src/App.tsx`.

**Q: How do I serve custom NFT images?**  
A: Place images in `public/` and reference them with a relative path in your contract metadata.

## 🤝 Contributing

PRs and issues welcome! Please open an issue if you have questions or suggestions.

**Happy building on Farcaster + Arbitrum!**

