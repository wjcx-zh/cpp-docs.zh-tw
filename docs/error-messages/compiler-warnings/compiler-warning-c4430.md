---
title: 編譯器警告 C4430 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4430
dev_langs:
- C++
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79c0045b568a24ad6702e748e82a8ebd88c41044
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093918"
---
# <a name="compiler-warning-c4430"></a>編譯器警告 C4430

遺漏類型規範 - 假設為 int。 注意： C + + 不支援 default-int

針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致此錯誤： 所有宣告都必須明確都指定類型;不會再假設為 int。

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