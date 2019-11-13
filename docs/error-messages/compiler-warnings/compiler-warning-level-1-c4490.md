---
title: 編譯器警告（層級1） C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: 41fa124eed365b87b419a4019262c0c673399295
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966185"
---
# <a name="compiler-warning-level-1-c4490"></a>編譯器警告（層級1） C4490

' override '：覆寫規範的使用不正確;' function ' 與基底 ref 類別方法不符

不正確地使用了覆寫規範。 例如，您不會覆寫介面函式，而是執行它。

如需詳細資訊，請參閱覆[寫](../../extensions/override-specifiers-cpp-component-extensions.md)規範。

## <a name="example"></a>範例

下列範例會產生 C4490。

```cpp
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```