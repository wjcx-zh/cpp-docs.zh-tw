---
title: 編譯器警告（層級1） C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 0ffc4c4aeb7d37ffa45f503a34fd369d36c00ce4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164205"
---
# <a name="compiler-warning-level-1-c4042"></a>編譯器警告（層級1） C4042

' identifier '：具有錯誤的儲存類別

在此內容中，指定的儲存類別無法搭配此識別碼使用。 編譯器會改為使用預設的儲存類別：

- `extern`，如果*identifier*是函數。

- 如果*identifier*是型式參數或區域變數，則為**auto**。

- 如果*identifier*是全域變數，則沒有儲存類別。

這項警告的原因可能是在參數宣告中指定**register**以外的儲存類別。

下列範例會產生 C4042

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```
