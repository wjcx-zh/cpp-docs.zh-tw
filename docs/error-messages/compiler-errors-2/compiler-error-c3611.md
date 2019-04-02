---
title: 編譯器錯誤 C3611
ms.date: 11/04/2016
f1_keywords:
- C3611
helpviewer_keywords:
- C3611
ms.assetid: 42f3e320-41de-420a-bd05-8924cab765aa
ms.openlocfilehash: 2d4c5cb02b1b8c5472502380fe7c74ff4a91954a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781922"
---
# <a name="compiler-error-c3611"></a>編譯器錯誤 C3611

'function': 密封函式不能有純規範

密封的函式宣告不正確。  如需詳細資訊，請參閱 <<c0> [ 密封](../../extensions/sealed-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3611。

```
// C3611.cpp
// compile with: /clr /c

ref struct V {
   virtual void Test() sealed = 0;   // C3611
   virtual void Test2() sealed;   // OK
   virtual void Test3() = 0;   // OK
};
```