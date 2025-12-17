# Wallet
# app id dd7ac22c-e616-4923-b321-ca1e7baf34cf
# sdk 
// Using npm
npm install @phantom/react-sdk
// Using yarn
yarn add @phantom/react-sdk
// Using pnpm
pnpm add @phantom/react-sdk
# getting started with the sdk 
import { PhantomProvider, useModal, darkTheme, usePhantom, AddressType } from "@phantom/react-sdk";

function App() {
  return (
    <PhantomProvider
      config={{
        providers: ["google", "apple", "injected"], // Enabled auth methods
        appId: "dd7ac22c-e616-4923-b321-ca1e7baf34cf",
        addressTypes: ["Ethereum","Solana","BitcoinSegwit","Sui"],
        authOptions: {
          redirectUrl: "https://yourapp.com/auth/callback", // Must be whitelisted in Phantom Portal
        },
      }}
      theme={darkTheme}
      appIcon="https://phantom-portal20240925173430423400000001.s3.ca-central-1.amazonaws.com/icons/5a712be6-3157-47e8-950d-27e16ab0bba9.jpg"
      appName="Diamante "
    >
      <WalletComponent />
    </PhantomProvider>
  );
}

function WalletComponent() {
  const { open, close, isOpened } = useModal();
  const { isConnected, user } = usePhantom();

  if (isConnected) {
    return (
      <div>
        <p>Connected</p>
      </div>
    );
  }

  return <button onClick={open}>Connect Wallet</button>;
}
