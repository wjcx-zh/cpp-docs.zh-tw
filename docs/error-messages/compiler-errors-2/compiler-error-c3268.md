---
title: 編譯器錯誤 C3268
ms.date: 11/04/2016
f1_keywords:
- C3268
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
ms.openlocfilehash: 191456a1e290b568897ba76cd5bdccb8f83c310b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201457"
---
# <a name="compiler-error-c3268"></a>編譯器錯誤 C3268

> '*function*'：泛型類別的泛型函數或成員函式不能有變數參數清單

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3268。

```cpp
// C3268.cpp
// compile with: /clr:pure /c
generic <class ItemType>
void Test(ItemType item, ...) {}   // C3268
// try the following line instead
// void Test(ItemType item) {}

generic <class ItemType2>
ref struct MyStruct { void Test(...){} };   // C3268
// try the following line instead
// ref struct MyStruct { void Test2(){} };   // OK
```
