---
title: 編譯器錯誤 C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: c52a0a4c4255eeed5f49a7e6c1e86a1f64b8ad77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755651"
---
# <a name="compiler-error-c3063"></a>編譯器錯誤 C3063

運算子 ' operator '：所有運算元都必須具有相同的列舉類型

在枚舉器上使用運算子時，兩個運算元都必須是列舉類型。 如需詳細資訊，請參閱[如何：在/cli 中C++定義和使用](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)列舉。

## <a name="example"></a>範例

下列範例會產生 C3063，並顯示如何修正此問題：

```cpp
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```
