---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: fddfc2e3295552414a00692006ab12725dc07d52
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213108"
---
# <a name="void-c"></a>void (C++)

當做函式傳回型別使用時， **`void`** 關鍵字會指定函式不會傳回值。 當用於函式的參數清單時， **`void`** 會指定函式不接受任何參數。 在指標的宣告中使用時， **`void`** 會指定指標為「通用」。

如果指標的類型為**void \* **，指標可以指向未使用或關鍵字宣告的任何變數 **`const`** **`volatile`** 。 除非**將 \* void**指標轉換成另一種類型，否則無法將其解除引用。 **Void \* **指標可以轉換成任何其他類型的資料指標。

**`void`** 指標可以指向函式，而不是 c + + 中的類別成員。

您不能宣告類型為的變數 **`void`** 。

## <a name="example"></a>範例

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[內建類型](../cpp/fundamental-types-cpp.md)
