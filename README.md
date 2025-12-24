# 🤖 Bitkub DCA Bot

> **Automate your crypto accumulation with precision and ease.**

Checking the charts every day is exhausting. The **Bitkub DCA Bot** is a lightweight, robust Python tool designed to automate your Dollar-Cost Averaging (DCA) strategy on the [Bitkub Exchange](https://www.bitkub.com/). whether you're stacking sats or accumulating your favorite altcoins, this bot ensures you stay consistent without the emotional stress of manual trading.

## ✨ Features

- **🚀 Smart Synchronization**: Automatically syncs with Bitkub server time to eliminate "Invalid Timestamp" errors.
- **🔐 Enterprise-Grade Security**: Implements standard HMAC-SHA256 signature authentication for secure API requests.
- **⚙️ Zero-Code Configuration**: Fully configurable via environment variables—perfect for CI/CD pipelines (GitHub Actions) or Docker.
- **🛡 Robust Error Handling**: Provides clear, actionable feedback for common issues like invalid symbols or permission errors.
- **⚡️ Lightweight**: Built with minimal dependencies, ensuring fast execution and low resource usage.

## 🛠 Prerequisites

- Python 3.6+
- A [Bitkub Account](https://www.bitkub.com/) with API access enabled.

## 📦 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/PattoMotto/bitkub-dca-bot.git
   cd bitkub-dca-bot
   ```

2. **Install dependencies**
   ```bash
   pip install requests
   ```

## ⚙️ Configuration

The bot is configured entirely through **Environment Variables**, making it secure and easy to deploy anywhere.

| Variable | Description | Default | Required |
|----------|-------------|---------|----------|
| `API_KEY` | Your Bitkub API Public Key | - | **Yes** |
| `API_SECRET` | Your Bitkub API Secret Key | - | **Yes** |
| `BUY_AMOUNT` | The amount of THB to spend per transaction | `108` | No |
| `SYMBOL` | The trading pair to buy (e.g., `ETH_THB`) | `BTC_THB` | No |

## 🚀 Usage

### 1. Local Execution
You can run the bot directly from your terminal.

**Linux/macOS:**
```bash
export API_KEY="your_actual_api_key"
export API_SECRET="your_actual_api_secret"
export BUY_AMOUNT="1000"
export SYMBOL="ETH_THB"

python main.py
```

**Windows (PowerShell):**
```powershell
$env:API_KEY="your_actual_api_key"
$env:API_SECRET="your_actual_api_secret"
$env:BUY_AMOUNT="1000"
$env:SYMBOL="ETH_THB"

python main.py
```

### 2. Output Example
When successful, the bot provides a clear summary of the transaction:
```text
🕒 Time: 1703421234567
🚀 Buying 108.0 THB of BTC_THB...
✅ SUCCESS!
   Order ID: 12345678
   Credit Used: 108.0
```

## 🤖 Automating with GitHub Actions (Recommended)

This bot is pre-configured with a powerful GitHub Actions workflow (`.github/workflows/dca_bot.yml`) that supports both automated scheduling and manual triggers.

### 1. Setup Secrets & Environment
1. Go to your repository **Settings** > **Environments**.
2. Create a new environment named `production`.
3. Add your `API_KEY` and `API_SECRET` as **Environment Secrets** within the `production` environment.

### 2. Schedule Options
By default, the bot runs **Daily**. You can customize this by uncommenting your preferred schedule in `.github/workflows/dca_bot.yml`:

- **Daily**: `0 2 * * *` (09:00 AM Bangkok Time) <-- **Default**
- **Weekly**: `0 2 * * 1` (Monday at 09:00 AM)
- **Hourly**: `0 * * * *`
- **Every 12 Hours**: `0 2,14 * * *`

### 3. Manual Trigger (Run on Demand)
You can manually trigger the bot to make an immediate purchase with custom parameters:
1. Go to the **Actions** tab in your repository.
2. Select **DCA Bot** from the left sidebar.
3. Click **Run workflow**.
4. (Optional) Enter a custom `Amount to Buy` (default: 108) and `Crypto Pair` (default: BTC_THB).
5. Click **Run workflow**.

## ⚠️ Disclaimer

This software is for educational purposes only. Automated trading carries risks. Ensure you test with small amounts and understand the code before using significant funds. The authors are not responsible for any financial losses.

---
*Maintained by PattoMotto*
