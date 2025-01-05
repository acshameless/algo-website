<img src="https://gw.alipayobjects.com/zos/k/h5/hzL4LG.jpg" width="800" />

<small>封面图摄于安吉晚饭黄昏，伴随着一点凉风吹来，还挺有意境的。</small>



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

