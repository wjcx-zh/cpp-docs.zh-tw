---
title: 編譯器錯誤 C3799
ms.date: 11/04/2016
f1_keywords:
- C3799
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
ms.openlocfilehash: 19ff414bde9bb24fca62fd10cfef6d18109199e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553539"
---
# <a name="compiler-error-c3799"></a>編譯器錯誤 C3799

索引的屬性不能有空參數清單

索引的屬性宣告不正確。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用屬性，在 C + + /cli CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3799，並示範如何修正此問題。

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