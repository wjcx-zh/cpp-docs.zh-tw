---
title: 編譯器錯誤 C3799
ms.date: 11/04/2016
f1_keywords:
- C3799
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
ms.openlocfilehash: 980683ebc2e086e4c16180f04466af9dbdd49d02
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165648"
---
# <a name="compiler-error-c3799"></a>編譯器錯誤 C3799

已編制索引的屬性不能有空白的參數清單

索引屬性宣告不正確。 如需詳細資訊，請參閱[如何：在/cli C++中使用屬性](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3799，並顯示如何修正此問題。

```cpp
// C3799.cpp
// compile with: /clr /c
ref struct C {
   property int default[] {   // C3799
   // try the following line instead
   // property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};
```
