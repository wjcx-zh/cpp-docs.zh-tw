---
title: 編譯器錯誤 C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205318"
---
# <a name="compiler-error-c2461"></a>編譯器錯誤 C2461

> '*class*'：不存在型式參數的函式語法

類別的函式不會指定任何型式參數。 函式的宣告必須指定正式參數清單。 清單可以是空的。

若要修正此問題，請在*類別*：:**類別*的宣告後面加入一對括弧。

## <a name="example"></a>範例

下列範例顯示如何修正 C2461：

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```
