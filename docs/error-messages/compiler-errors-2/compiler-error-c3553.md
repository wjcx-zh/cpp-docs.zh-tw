---
title: 編譯器錯誤 C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 82540e0f6c4b60aea2e708dcf00796490cd7d3cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200651"
---
# <a name="compiler-error-c3553"></a>編譯器錯誤 C3553

> decltype 必須是運算式而不是類型

`decltype()` 關鍵字需要運算式作為引數，而不是類型名稱。 例如，下列程式碼片段的最後一個陳述式會產生錯誤 C3553。

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```
