---
title: 編譯器警告 （層級 3） C4334 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b7bb16ea38b2c2112c12c561398341a7d1adbfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044011"
---
# <a name="compiler-warning-level-3-c4334"></a>編譯器警告 (層級 3) C4334

'operator': 32 位元移位的結果會隱含地轉換為 64 位元 （是 64 位元位移？）

32 位元移位的結果會隱含地轉換至 64 位元和 64 位元位移預定編譯器懷疑。  若要解決這個警告，使用 64 位元位移，或是明確轉換為 64 位元位移結果。

## <a name="example"></a>範例

下列範例會產生 C4334。

```
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```