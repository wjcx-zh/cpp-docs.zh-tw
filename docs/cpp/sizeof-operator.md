---
title: sizeof 運算子
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 13e181bf84e359d433fbe951b1aa69320a1f0013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186291"
---
# <a name="sizeof-operator"></a>sizeof 運算子

根據類型的大小，產生其運算元的大小 **`char`** 。

> [!NOTE]
> 如需運算子的詳細資訊 `sizeof ...` ，請參閱[省略號和 variadic 範本](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>語法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>備註

運算子的結果屬於 **`sizeof`** 類型，也就是 `size_t` 包含檔案中所定義的整數類資料類型 \<stddef.h> 。 這個運算子可以避免在您的程式中指定與電腦相關的資料大小。

的運算元 **`sizeof`** 可以是下列其中一項：

- 類型名稱。 若要搭配 **`sizeof`** 型別名稱使用，名稱必須以括弧括住。

- 運算式。 與運算式搭配使用時， **`sizeof`** 可以使用或不搭配括弧來指定。 並不會評估運算式。

當 **`sizeof`** 運算子套用至類型的物件時 **`char`** ，它會產生1。 當 **`sizeof`** 運算子套用至陣列時，它會產生該陣列中的總位元組數，而不是陣列識別碼所表示的指標大小。 若要取得陣列識別碼所表示的指標大小，請將它當做參數傳遞至使用的函式 **`sizeof`** 。 例如：

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

當 **`sizeof`** 運算子套用至 **`class`** 、 **`struct`** 或類型時 **`union`** ，結果會是該類型物件中的位元組數目，加上加入以對齊字邊界上成員的任何填補。 在加上個別成員的儲存需求之後，其結果不一定會對應計算的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)編譯器選項和[pack](../preprocessor/pack.md) pragma 會影響成員的對齊界限。

**`sizeof`** 即使是空的類別，運算子也永遠不會產生0。

**`sizeof`** 運算子不能與下列運算元搭配使用：

- 函數。 （不過，可以套用至函式的 **`sizeof`** 指標）。

- 位元欄位。

- 未定義的類別。

- 型別 **`void`** 。

- 以動態方式配置的陣列。

- 外部陣列。

- 不完整的類型。

- 以括號括住的不完整類型名稱。

當 **`sizeof`** 運算子套用至參考時，其結果會與 **`sizeof`** 已套用至物件本身相同。

如果可變大小陣列是結構的最後一個元素，則 **`sizeof`** 運算子會傳回不含陣列的結構大小。

**`sizeof`** 運算子通常用來計算陣列中的元素數目，其使用的運算式格式如下：

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
