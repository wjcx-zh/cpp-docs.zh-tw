---
title: 編譯器錯誤 C2071 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2071
dev_langs:
- C++
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faee56023d14e9b010d1c691af654ffcbc31dc78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169201"
---
# <a name="compiler-error-c2071"></a>編譯器錯誤 C2071
'identifier'：儲存類別不合法  
  
 `identifier` 已宣告為無效[儲存類別](../../c-language/c-storage-classes.md)。 當指定了一個以上的儲存類別給識別項，或是定義與儲存類別宣告不相容時，可能會造成這個錯誤。  
  
 若要修正這個問題，了解識別項的預定的儲存類別 — 比方說，`static`或`extern`— 並更正宣告以符合。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2071。  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C2071。  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```