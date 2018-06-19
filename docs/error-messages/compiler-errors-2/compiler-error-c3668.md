---
title: 編譯器錯誤 C3668 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3668
dev_langs:
- C++
helpviewer_keywords:
- C3668
ms.assetid: 53a96698-bde4-4447-95b5-b5108291f60c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2261b0a700e312d6acdf56377bf56c05d971a17e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266525"
---
# <a name="compiler-error-c3668"></a>編譯器錯誤 C3668
'method': 具有覆寫規範 'override' 方法不會覆寫任何基底類別方法  
  
 函式嘗試覆寫函式不存在。  
  
 如需詳細資訊，請參閱[明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3668。  
  
```  
// C3668.cpp  
// compile with: /c  
__interface I {  
   void f(int);   // virtual by default  
};  
  
class J {  
public:  
   void g(int);  
   virtual void h(int);  
};  
  
struct R : I,J {  
   virtual void f() override {}   // C3668  
   virtual void f(int) override {}   // OK  
  
   virtual void g(int) override {}   // C3668  
   virtual void h(int) override {}   // OK  
};  
```