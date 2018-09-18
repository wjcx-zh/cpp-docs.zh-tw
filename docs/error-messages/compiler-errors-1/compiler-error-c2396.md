---
title: 編譯器錯誤 C2396 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2396
dev_langs:
- C++
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d69dfc1e296532f00ce9f44a178a366dca41e2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061626"
---
# <a name="compiler-error-c2396"></a>編譯器錯誤 C2396

' your_type:: operator'type ': 有效 CLR 或 WinRT 使用者定義的轉換 functionnot。 必須從下列項目轉換或轉換為下列項目：'T^'、'T^%'、'T^&'，其中 T = 'your_type'

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