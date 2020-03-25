---
title: 編譯器警告 (層級 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 38b93c83f822bc5b856a46f0dd62ea275d2bf207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198714"
---
# <a name="compiler-warning-level-3-c4334"></a>編譯器警告 (層級 3) C4334

' operator '： 32-位移位的結果隱含轉換成64位（預期為64位移位？）

32位移位的結果會隱含轉換成64位，而編譯器會懷疑有64位的移位。  若要解決這個警告，請使用 64-bit shift，或將移位結果明確轉換為64位。

## <a name="example"></a>範例

下列範例會產生 C4334。

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```
