---
title: 編譯器錯誤 C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744832"
---
# <a name="compiler-error-c2396"></a>編譯器錯誤 C2396

' your_type：： operator'type ' '： CLR 或 WinRT 使用者定義轉換 functionnot 有效。 必須轉換成，或轉換成： t ^ '，t ^% '，t ^ & '，其中 T = ' your_type '

Windows 執行階段或受管理的類型中的轉換函式沒有至少一個參數，其類型與包含轉換函式的類型相同。

下列範例會產生 C2396，並示範如何修正此問題：

```cpp
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
