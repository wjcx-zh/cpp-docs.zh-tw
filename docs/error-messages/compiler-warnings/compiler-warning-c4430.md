---
title: 編譯器警告 C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: 091d988a5af277e78a2954eb5b0b95bc64c56069
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165258"
---
# <a name="compiler-warning-c4430"></a>編譯器警告 C4430

遺漏類型規範 - 假設為 int。 注意： C++不支援 default-int

此錯誤可能是因為針對 Visual Studio 2005 而完成的編譯器一致性工作所產生：所有宣告都必須明確指定類型;已不再假設為 int。

C4430 一律會發出為錯誤。  您可以使用 `#pragma warning` 或 **/wd**關閉此警告;如需詳細資訊，請參閱[warning](../../preprocessor/warning.md)或[/w、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/wo、/Wv、/Wx （警告層級）](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>範例

下列範例會產生 C4430。

```cpp
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
