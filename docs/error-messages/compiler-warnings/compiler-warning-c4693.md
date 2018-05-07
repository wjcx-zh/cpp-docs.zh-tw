---
title: 編譯器警告 C4693 |Microsoft 文件
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4693
dev_langs:
- C++
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8230e60d65c80b4f839cc8a1c97ccc0c7b18086
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4693"></a>編譯器警告 C4693

> 'class': 密封的抽象類別不能有任何執行個體成員 'Test'

如果類型標記[密封](../../windows/sealed-cpp-component-extensions.md)和[抽象](../../windows/abstract-cpp-component-extensions.md)，它只能有靜態成員。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。

## <a name="example"></a>範例

下例會產生 C4693。

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```