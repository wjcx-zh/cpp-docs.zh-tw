---
title: "編譯器錯誤 C3662 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3662
dev_langs:
- C++
helpviewer_keywords:
- C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c056d8ff06a44623f362c2f9542af7f7d389b65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3662"></a>編譯器錯誤 C3662
'member'：只允許在 Managed 或 WinRT 類別的成員函式上覆寫規範 'specifier'  
  
 不允許在原生類型的成員上使用覆寫規範。  
  
 如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3662。  
  
```  
// C3662.cpp  
// compile with: /clr /c  
struct S {  
   virtual void f();  
};  
  
struct S1 : S {  
   virtual void f() new;   // C3662  
};  
  
ref struct T {  
   virtual void f();  
};  
  
ref struct T1 : T {  
   virtual void f() new;   // OK  
};  
```