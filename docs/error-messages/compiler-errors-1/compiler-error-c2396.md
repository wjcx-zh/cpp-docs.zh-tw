---
title: 編譯器錯誤 C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303511"
---
# <a name="compiler-error-c2396"></a>編譯器錯誤 C2396

' your_type:: operator'type ':CLR 或 WinRT 使用者定義的轉換 functionnot 有效。 必須轉換自或轉換成：'T ^'、' T ^ %'，' T ^ &'，其中 T = 'your_type'

Windows 執行階段或受管理的類型中的轉換函式沒有至少一個參數，其類型與包含轉換函式的類型相同。

下列範例會產生 C2396，並示範如何修正此問題：

```
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```