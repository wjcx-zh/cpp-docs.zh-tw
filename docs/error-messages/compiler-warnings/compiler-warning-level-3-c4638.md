---
title: 編譯器警告 (層級 3) C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: 3662116359f906ef6f0a004fada8efd6771d0a0a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174124"
---
# <a name="compiler-warning-level-3-c4638"></a>編譯器警告 (層級 3) C4638

> XML 檔批註目標：參考未知的符號 '*symbol*'

## <a name="remarks"></a>備註

編譯器無法解析符號 (*符號*)。 符號在編譯中必須有效。

## <a name="example"></a>範例

下列範例會產生 C4638：

```cpp
// C4638.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary> Text </summary>
   /// <see cref="aSymbolThatAppearsNowhereInMyProject"/>
   // Try the following line instead:
   // /// <see cref="System::Console::WriteLine"/>
   void MyMethod() {}
};   // C4638
```
