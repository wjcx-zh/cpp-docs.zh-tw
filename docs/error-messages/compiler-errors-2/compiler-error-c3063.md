---
title: 編譯器錯誤 C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 9e53d9fe273a392695212df6dbeb679822a39068
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404210"
---
# <a name="compiler-error-c3063"></a>編譯器錯誤 C3063

運算子 'operator': 所有運算元必須都具有相同的列舉類型

當使用列舉值的運算子，兩個運算元必須是列舉型別。 如需詳細資訊，請參閱[如何：定義和使用列舉在C++/CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3063，並示範如何修正此問題：

```
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```