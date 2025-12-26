
- **Load average** = These values are the number of processes waiting for the CPU or using it in the given period.
- Displayed as **1, 5, 15 min averages** (`uptime` or `top`).

#### **Load Meaning (on an 8-core CPU):**

**an ideal case scenario**

| Load Avg | Meaning                                                                                      |
| -------- | -------------------------------------------------------------------------------------------- |
| **1.0**  | 1 core fully used, 7 idle (12.5% CPU usage) or 12.5% CPU usage is shared among all the cores |
| **4.0**  | 4 cores used, 4 idle (50% CPU usage) or 50% CPU usage is shared among all the cores          |
| **8.0**  | All 8 cores fully utilized (100% CPU usage) or 100% CPU usage is shared among all the cores  |
| **12.0** | CPU overloaded (8 busy, 4 waiting).                                                          |
|          |                                                                                              |

#### **Key Takeaways:**

✅ **Load < Cores** → No CPU bottleneck.  
⚠️ **Load = Cores** → Fully utilized but no waiting.  
❌ **Load > Cores** → Overloaded, performance degrades.

🔍 **Check Load:**

```bash
uptime
top
htop
```

✅ **Load average does NOT directly show per-core usage.**  
✅ **A load of 1 means 1 unit of CPU capacity is used, but it might be spread across cores.**