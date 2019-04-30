---
title: 編譯器錯誤 C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: ab18381d3f263e3207662e1667ac5c835983412f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344497"
---
# <a name="compiler-error-c3612"></a>編譯器錯誤 C3612

'type': 密封的類別不能為抽象

使用所定義的型別`value`密封格式，根據預設，和類別是抽象的除非它會實作其基底的所有方法。 密封的抽象類別都可以是基底類別，也可以它具現化。

如需詳細資訊，請參閱 <<c0> [ 類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3612:

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```