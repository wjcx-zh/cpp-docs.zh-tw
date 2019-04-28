---
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: ece1016b7a18873dfa477b0f8b6ae4271a0f8001
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301483"
---
# <a name="property-c"></a>property (C++)

**Microsoft 專屬**

這個屬性可以套用至類別或結構定義中的非靜態「虛擬資料成員」。 編譯器會將這些「虛擬資料成員」的參考變更為函式呼叫，將它們視為資料成員。

## <a name="syntax"></a>語法

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>備註

當編譯器看到成員選取運算子右側以此屬性宣告的資料成員 ("**。**「 或 」**->**")，它會將轉換作業`get`或`put`函式，根據這類運算式為左值或右值。 在更複雜的內容，例如"`+=`"，重寫藉由同時執行`get`和`put`。

在類別或結構定義中也可以使用這個屬性宣告空陣列。 例如: 

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

上述陳述式表示可以同時使用 `x[]` 和一個或多個陣列索引。 在這種情況下，`i=p->x[a][b]` 會轉換為 `i=p->GetX(a, b)`，而 `p->x[a][b] = i` 則會轉換為 `p->PutX(a, b, i);`

**結束 Microsoft 專屬**

## <a name="example"></a>範例

```cpp
// declspec_property.cpp
struct S {
   int i;
   void putprop(int j) {
      i = j;
   }

   int getprop() {
      return i;
   }

   __declspec(property(get = getprop, put = putprop)) int the_prop;
};

int main() {
   S s;
   s.the_prop = 5;
   return s.the_prop;
}
```

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)