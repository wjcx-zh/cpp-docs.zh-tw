---
title: "編譯器錯誤 C3764 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3764
dev_langs:
- C++
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 60317bb31b5021d4b9b1b6568d77ae92e06880ce
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3764"></a>編譯器錯誤 C3764
'override_function': 無法覆寫基底類別方法 'base_class_function'  
  
 編譯器偵測到格式不正確的覆寫。 例如，基底類別函式未`virtual`。 如需詳細資訊，請參閱[覆寫](../../windows/override-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3764。  
  
```  
// C3764.cpp  
// compile with: /clr /c  
public ref struct A {  
   void g(int);  
   virtual void h(int);  
};  
  
public ref struct B : A {  
   virtual void g(int) override {}   // C3764  
   virtual void h(int) override {}   // OK  
};  
```  
  
## <a name="example"></a>範例  
 C3764 基底類別方法同時為明確時，也會發生和具名覆寫。 下列範例會產生 C3764。  
  
```  
// C3764_b.cpp  
// compile with: /clr /c  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : public A {  
   virtual void Test() override {}  
   virtual void Test2() = A::Test {}   // C3764  
};  
```
