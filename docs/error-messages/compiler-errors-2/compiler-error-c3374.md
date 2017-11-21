---
title: "編譯器錯誤 C3374 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3374
dev_langs: C++
helpviewer_keywords: C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 16c857cf431462abd2acc21cf7444ec0aad2d075
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3374"></a>編譯器錯誤 C3374
無法取得 'function' 的位址，除非建立委派執行個體  
  
 除了建立委派執行個體之外，已在內容中取得函式的位址。  
  
 下列範例會產生 C3374：  
  
```  
// C3374.cpp  
// compile with: /clr  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      System::Console::WriteLine("in func1 {0}", i);  
   }  
};  
  
int main() {  
   &A::func1;   // C3374  
  
   // OK  
   A ^ a = gcnew A;  
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何：定義和使用委派 (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)