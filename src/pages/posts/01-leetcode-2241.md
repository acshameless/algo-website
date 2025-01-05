---

title: "LeetCode 2241" 

date: "2025-01-01" 

tags: ["leetcode", "programming"] 

---

https://leetcode.cn/problems/design-an-atm-machine/

```python3
class ATM:
    def __init__(self):
        self.banknotes = [0, 0, 0, 0, 0]  # 0:20, 1:50, 2:100, 3:200, 4:500

    def deposit(self, banknotesCount):
        for i in range(5):
            self.banknotes[i] += banknotesCount[i]

    def withdraw(self, amount):
        denominations = [500, 200, 100, 50, 20]
        result = [0, 0, 0, 0, 0]  # 0:20, 1:50, 2:100, 3:200, 4:500
        temp_banknotes = self.banknotes.copy()
        
        for i in range(5):
            deno = denominations[i]
            banknote_index = 4 - i
            count = min(amount // deno, temp_banknotes[banknote_index])
            result[4 - i] = count
            amount -= count * deno
            temp_banknotes[banknote_index] -= count
        
        if amount != 0:
            return [-1]
        else:
            self.banknotes = temp_banknotes
            return result	
```

