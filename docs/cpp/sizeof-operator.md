---
title: sizeof 運算子
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 9edd6420193fbc1ff6013c545b294851ce105848
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267215"
---
# <a name="sizeof-operator"></a>sizeof 運算子

會產生其運算元的類型大小的大小**char**。

> [!NOTE]
>  如需`sizeof ...`運算子，請參閱[省略符號和 Variadic 範本](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>語法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>備註

結果**sizeof**運算子是型別的`size_t`，在 include 檔中定義的整數類資料類型\<stddef.h >。 這個運算子可以避免在您的程式中指定與電腦相關的資料大小。

運算元**sizeof**可以是下列其中之一：

- 類型名稱。 若要使用**sizeof**與類型名稱，名稱必須括在括號。

- 一個運算式。 運算式，搭配使用時**sizeof**可以使用或不使用括號指定。 並不會評估運算式。

當**sizeof**運算子套用至型別的物件**char**，它會產生 1。 當**sizeof**運算子套用至陣列，它會將該陣列，而不是陣列識別項所表示的指標的大小中的位元組總數。 若要取得陣列識別項所表示的指標的大小，將它傳遞做為參數來使用的函式**sizeof**。 例如: 

## <a name="example"></a>範例

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>範例輸出

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

當**sizeof**運算子套用至**類別**，**結構**，或**union**型別，結果是該物件中的位元組數目型別，再加上任何新增至對齊字邊界上的成員的填補。 在加上個別成員的儲存需求之後，其結果不一定會對應計算的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)編譯器選項和[組件](../preprocessor/pack.md)pragma 會影響成員的對齊界限。

**Sizeof**運算子永遠不會產生 0，即使用於空類別。

**Sizeof**運算子不能與下列運算元：

- 函式。 (不過， **sizeof**可以套用至函式的指標。)

- 位元欄位。

- 未定義的類別。

- 型別**void**。

- 以動態方式配置的陣列。

- 外部陣列。

- 不完整的類型。

- 以括號括住的不完整類型名稱。

當**sizeof**運算子套用至參考，結果會是相同如同**sizeof**必須已套用至物件本身。

如果可變大小的陣列是結構中的最後一個元素**sizeof**運算子會傳回不含陣列結構的大小。

**Sizeof**運算子通常用來計算陣列使用表單的運算式中的項目數：

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)