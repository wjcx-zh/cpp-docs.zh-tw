---
title: 編譯器警告（層級3） C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: ebebfe9994be3dd136e3924cb2aea60c0c901926
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051627"
---
# <a name="compiler-warning-level-3-c4334"></a>編譯器警告（層級3） C4334

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