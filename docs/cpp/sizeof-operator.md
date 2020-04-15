---
title: sizeof 運算子
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 8789bb5e0e363458edffa7207ea1e138aae4d284
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365573"
---
# <a name="sizeof-operator"></a>sizeof 運算子

相對於**字元**類型的大小,生成其操作數的大小。

> [!NOTE]
> 有關運算子的資訊,`sizeof ...`請參考[圓和瓦里亞迪奇樣本](../cpp/ellipses-and-variadic-templates.md)。

## <a name="syntax"></a>語法

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>備註

**大小運算符**的結果為類型`size_t`,在包含\<檔 stddef.h>中定义的积分类型。 這個運算子可以避免在您的程式中指定與電腦相關的資料大小。

**大小**操作數可以是以下操作數之一:

- 類型名稱。 要使用 具有類型名稱**的大小**,名稱必須包含在括弧中。

- 運算式。 當與運算式一起使用時,可以使用或沒有括弧指定**size。** 並不會評估運算式。

當**sizeof**運算元應用於**字元**類型的物件時,它會產生 1。 當**sizeOF**運算子應用於陣列時,它將生成該陣列中的位元組總數,而不是數位標識符表示的指標的大小。 要取得數位識別碼表示的指標的大小,請將其作為參數傳遞給使用**size 的**函數。 例如：

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

當**sizeof**運算子應用於**類**、**結構**類型或**聯合**類型時,結果是該類型物件中的位元組數,以及為對齊單詞邊界上的成員添加的任何填充。 在加上個別成員的儲存需求之後，其結果不一定會對應計算的大小。 [/Zp](../build/reference/zp-struct-member-alignment.md)編譯器選項和[包](../preprocessor/pack.md)雜注會影響成員的對齊邊界。

即使對於空類,**大小運算子**也永遠不會產生 0。

**大小運算子**不能與以下操作數一起使用:

- 函數。 (但是,**大小**可以應用於指向函數的指標。

- 位元欄位。

- 未定義的類別。

- 型**態 void**。

- 以動態方式配置的陣列。

- 外部陣列。

- 不完整的類型。

- 以括號括住的不完整類型名稱。

當**sizeOF**運算子應用於引用時,結果與將**sizesize**應用於物件本身的結果相同。

如果大小陣列是結構的最後一個元素,**則 sizeof**運算符返回沒有陣列的結構的大小。

**sizeof**運算子通常用於使用表單的運算子組中的元素數:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
