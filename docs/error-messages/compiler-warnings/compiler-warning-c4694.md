---
title: 編譯器警告 C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: daf5423588d08260239c3cff5a68532a358d07b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165115"
---
# <a name="compiler-warning-c4694"></a>編譯器警告 C4694

> '*class*'：密封抽象類別不能有基類 '*base_class*'

抽象和密封類別無法從參考類型繼承，密封和抽象類別無法實作基底類別函式，也不允許自己用作為基底類別。

如需詳細資訊，請參閱[abstract](../../extensions/abstract-cpp-component-extensions.md)、 [sealed](../../extensions/sealed-cpp-component-extensions.md)和[類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。

此警告會自動升級為錯誤。 如果您想要修改此行為，請使用[#pragma 警告](../../preprocessor/warning.md)。

## <a name="example"></a>範例

下列範例會產生 C4694。

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
