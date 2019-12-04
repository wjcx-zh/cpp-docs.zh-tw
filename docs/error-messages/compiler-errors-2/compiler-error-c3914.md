---
title: 編譯器錯誤 C3914
ms.date: 11/04/2016
f1_keywords:
- C3914
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
ms.openlocfilehash: 6f7da67871b5e6b9d7da9a9aa4eebeb761f8cc50
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737994"
---
# <a name="compiler-error-c3914"></a>編譯器錯誤 C3914

預設屬性不可以是靜態的

預設屬性宣告不正確。  如需詳細資訊，請參閱[如何：在/cli C++中使用屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3914，並顯示如何修正此問題。

```cpp
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```
