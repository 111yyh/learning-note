# learning-note
项目问题
## 输入框限制字节数问题
项目要求：输入框限制32个字节数，超出部分截断
```
limitByte(value) {
      let encoder = new TextEncoder()
      let uint8Array = encoder.encode(value)
      let cutArray = uint8Array.subarray(0,31)
      let cutStr = new TextDecoder().decode(cutArray)
      const sample = /\uFFFD/g;
      for (let i = 0; i < cutStr.length; i++) {
        if (cutStr.charAt(i).match(sample)) {
          cutStr = cutStr.substring(0,i)
        }
      }
      return cutStr
    }
```
