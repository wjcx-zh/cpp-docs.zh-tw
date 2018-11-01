---
title: 編譯器錯誤 C2449
ms.date: 11/04/2016
f1_keywords:
- C2449
helpviewer_keywords:
- C2449
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
ms.openlocfilehash: f674bbec7cee8c00792848ee7e51b1e46299dd58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655316"
---
# <a name="compiler-error-c2449"></a>編譯器錯誤 C2449

找到 ' {' 在檔案範圍 （遺漏函式標頭？）

左大括號就會發生在檔案範圍中。

此錯誤可能因函式標頭和函式定義中的左大括號之間的分號。

下列範例會產生 C2499:

```
// C2449.c
// compile with: /c
void __stdcall func(void) {}   // OK
void __stdcall func(void);  // extra semicolon on this line
{                         // C2449 detected here
```