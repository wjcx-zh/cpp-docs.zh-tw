---
title: property (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: 03f71739698fd20a01fd72567ce5b9babc176327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179298"
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

當編譯器在成員選取運算子（" **.** " 或 " **->** "）右邊看到以這個屬性宣告的資料成員時，它會根據這類運算式是左值或右值，將作業轉換成 `get` 或 `put` 函數。 在更複雜的內容中（例如 "`+=`"），會同時執行 `get` 和 `put`來進行重寫。

在類別或結構定義中也可以使用這個屬性宣告空陣列。 例如：

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

上述陳述式表示可以同時使用 `x[]` 和一個或多個陣列索引。 在這種情況下，`i=p->x[a][b]` 會轉換為 `i=p->GetX(a, b)`，而 `p->x[a][b] = i` 則會轉換為 `p->PutX(a, b, i);`

**END Microsoft 特定的**

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
