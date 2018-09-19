---
title: 屬性 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- property_cpp
dev_langs:
- C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7388fd180da4bd82b343d193f62c30ff1069342
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064907"
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