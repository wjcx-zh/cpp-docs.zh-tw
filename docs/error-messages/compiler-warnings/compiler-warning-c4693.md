---
title: 編譯器警告 C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 71c3db18b400ce94bff3c643d6728a6613061039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165128"
---
# <a name="compiler-warning-c4693"></a>編譯器警告 C4693

> 'class': 密封的抽象類別不能有任何執行個體成員 'Test'

如果類型標記為[sealed](../../extensions/sealed-cpp-component-extensions.md)和[abstract](../../extensions/abstract-cpp-component-extensions.md)，則只能有靜態成員。

此警告會自動升級為錯誤。 如果您想要修改此行為，請使用[#pragma 警告](../../preprocessor/warning.md)。

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
