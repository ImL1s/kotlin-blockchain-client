# kotlin-blockchain-client

<p align="center">
  <img src="../docs/images/kmp_crypto_banner.png" alt="kotlin-blockchain-client" width="100%">
</p>

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/kotlin-2.0.21-blue.svg?logo=kotlin" alt="Kotlin"></a>
  <a href="#"><img src="https://img.shields.io/badge/multiplatform-android%20%7C%20ios%20%7C%20jvm-brightgreen" alt="Multiplatform"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache%202.0-blue.svg" alt="License"></a>
</p>

<p align="center">
  <strong>🌐 A lightweight, multiplatform blockchain client for Bitcoin and Ethereum.</strong>
</p>

<p align="center">
  Built with Ktor and Kotlinx.serialization. Provides a unified API to interact with Mempool.space (Bitcoin) and standard JSON-RPC nodes (Ethereum).
</p>

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Bitcoin REST** | Full integration with Mempool.space API for UTXOs, transactions, and fees. |
| **Ethereum RPC** | Standard JSON-RPC client for EVM chains (Infura, Alchemy, etc.). |
| **Multiplatform** | Supports Android, iOS, and JVM. |
| **Fee Estimation** | Built-in recommended fee fetching. |

---

## 📦 Installation

```kotlin
// build.gradle.kts
commonMain.dependencies {
    implementation("io.github.iml1s:kotlin-blockchain-client:1.0.0")
}
```

---

## 🚀 Usage

### Bitcoin (Mempool.space)

```kotlin
val httpClient = HttpClient {
    install(ContentNegotiation) {
        json(Json { ignoreUnknownKeys = true })
    }
}

val btcClient = MempoolSpaceClient(httpClient)

// Get Balance
val balance = btcClient.getBalance("bc1q...")

// Get UTXOs
val utxos = btcClient.getUTXOs("bc1q...")

// Broadcast Transaction
val txId = btcClient.broadcastTransaction("020000...")
```

### Ethereum (JSON-RPC)

```kotlin
val evmClient = EvmJsonRpcClient(httpClient, "https://mainnet.infura.io/v3/YOUR_KEY")

// Get Nonce
val nonce = evmClient.getNonce("0x742d35Cc6634C0532925a3b844Bc454e4438f44e")

// Get Gas Price (EIP-1559 capable)
val fees = evmClient.getFeeRates()
println("Fast Gas: ${fees.fast}")
```
