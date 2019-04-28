---
title: 參考 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: aafc582299402eabab2736ac7d07b6c4c397413c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244210"
---
# <a name="references-c"></a>參考 (C++)

參考 (例如指標) 會儲存位在記憶體中其他位置之物件的位址。 與指標不同，參考在初始化之後不能參照不同的物件，或設為 null。 有兩種類型的參考： 左值參考參照具名變數，右值參考參照[暫存物件](../cpp/temporary-objects.md)。 & 運算子表示左值參考和 & & 運算子表示右值參考或 （右值或左值） 的通用參考內容而定。

參考可能是使用下列語法來宣告：

> \[*storage-class-specifiers*] \[*cv-qualifiers*] *type-specifiers* \[*ms-modifier*] *declarator* \[**=** *expression*]**;**

可能會使用任何有效的宣告子來指定參考。 除非參考是函式或陣列類型的參考，否則便會套用下列簡化的語法：

> \[*儲存類別規範*] \[ *cv 限定詞*]*型別規範* \[ **&** 或**&&**] \[ *cv 限定詞*]*識別碼* \[ **=** *運算式*]**;**

參考是使用下列序列宣告：

1. 宣告指定名稱：

   - 選擇性的儲存類別規範。

   - 選擇性**const**及/或**volatile**限定詞。

   - 類型指定名稱：類型的名稱。

1. 宣告子：

   - 選擇性的 Microsoft 專有修飾詞。 如需詳細資訊，請參閱 < [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)。

   - **&** 運算子或**&&** 運算子。

   - 選擇性**const**及/或**volatile**限定詞。

   - 識別碼。

1. 選擇性的初始設定式。

指標陣列和函式更複雜的宣告子形式也適用於陣列和函式的參考。 如需詳細資訊，請參閱 <<c0> [ 指標](../cpp/pointers-cpp.md)。

多個宣告子和初始設定式可能會出現在逗號分隔清單中，後面接著一個宣告指定名稱。 例如: 

```cpp
int &i;
int &i, &j;
```

參考、指標和物件可以同時宣告：

```cpp
int &ref, *ptr, k;
```

參考會保存物件的位址，不過其運作方式與物件相同。

在下列程式中，請注意物件的名稱 `s` 和物件的參考 `SRef` 在程式中的使用方式是相同的：

## <a name="example"></a>範例

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>另請參閱

[參考型別函式引數](../cpp/reference-type-function-arguments.md)<br/>
[參考型別函式傳回](../cpp/reference-type-function-returns.md)<br/>
[指標的參考](../cpp/references-to-pointers.md)
