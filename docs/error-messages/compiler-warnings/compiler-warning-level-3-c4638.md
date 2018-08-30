---
title: 編譯器警告 （層級 3） C4638 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4638
dev_langs:
- C++
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29febc17f041fee27064fc085896c892eecd5c56
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198228"
---
# <a name="compiler-warning-level-3-c4638"></a>編譯器警告 (層級 3) C4638

> XML 文件註解目標： 未知的符號參考 '*符號*'

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