# 🏦 Bank Account Simulation with Twilio SMS & Logging

This project demonstrates a simple **Bank Account System** in Python with:  
- 📲 **Twilio SMS Notifications**  
- 📝 **Integrated Logging System** (primary focus)  
- ⚡ **Custom Exception Handling**  
- 💵 **Deposit & Withdrawal Operations**  

---

## 📝 Logging System (Core Feature)

The system uses Python's built-in **`logging`** module to track all events:  
- ✅ Account creation  
- ✅ Successful withdrawals/deposits  
- ✅ Failed transactions (insufficient funds / invalid deposits)  
- ✅ SMS delivery status  
- ✅ Critical system errors  

### 🔧 Logging Configuration
```python
import logging

logging.basicConfig(
    filename='bank_transactions.log',
    level=logging.INFO
)

# Suppress excessive Twilio logs
logging.getLogger("twilio").setLevel(logging.WARNING)

# 📝 Logging Levels Overview

| 🔑 Log Level | 📝 Purpose | ✅ Example Use Case | 📂 Where It’s Stored |
|-------------|------------|---------------------|----------------------|
| **INFO**    | Records normal operations and successful events | Account created, Deposit/Withdrawal successful, SMS sent | `bank_transactions.log` |
| **WARNING** | Flags recoverable issues that don’t crash the system | Withdrawal failed (insufficient funds), Invalid deposit amount | `bank_transactions.log` |
| **ERROR**   | Logs serious problems, usually external failures | SMS sending failure due to Twilio API issue | `bank_transactions.log` |
| **CRITICAL**| Captures very severe errors that might stop the program | System crash, unexpected runtime errors | `bank_transactions.log` |

---

# 📜 Example Log Messages

| 🕒 Timestamp | 🔑 Level | 📝 Message |
|-------------|----------|------------|
| 2025-09-04 17:05:22 | INFO | Account created: 123456, Initial balance: ₹1000 |
| 2025-09-04 17:06:10 | INFO | Withdrawal of ₹500.00 successful. Available balance: ₹500.00 (Account: 123456) |
| 2025-09-04 17:07:02 | WARNING | Withdrawal failed: Insufficient funds for withdrawal (Account: 123456) |
| 2025-09-04 17:08:41 | INFO | Deposit of ₹200.00 successful. Available balance: ₹700.00 (Account: 123456) |
| 2025-09-04 17:09:18 | ERROR | Failed to send SMS to +918431565515: [TwilioError] |
| 2025-09-04 17:10:05 | CRITICAL | Unexpected error: Connection timeout |


