---
title: 編譯器警告 C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: fe765fa49b9aa11667e1eac4a9cfed54bb84fd8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447870"
---
# <a name="compiler-warning-c4430"></a>編譯器警告 C4430

遺漏類型規範 - 假設為 int。 注意:C++不支援 default-int

針對 Visual Studio 2005 所進行的編譯器一致性工作可能會導致此錯誤： 所有宣告都必須明確都指定類型;不會再假設為 int。

C4430 一律發出為錯誤。  您可以關閉此警告，其中含有`#pragma warning`或 **/wd**; 請參閱[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 / w3、 / w4、 /w1、 /w2、 / w3、 / w4、 /Wall、 /wd，/ /wo，我們 （警告層級）](../../build/reference/compiler-option-warning-level.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C4430。

```
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```