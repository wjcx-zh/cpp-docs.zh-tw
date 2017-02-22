---
title: "編譯器錯誤 C3181 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3181"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3181"
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C3181
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 運算子的運算元無效  
  
 傳遞給 [\_\_typeof](../../misc/typeof.md) 或 [typeid](../../windows/typeid-cpp-component-extensions.md) 運算子的參數無效。  參數必須是 Managed 型別。  
  
 請注意編譯器是使用對應至 Common Language Runtime 中型別之原生型別的別名。  
  
 下列範例會產生 C3181：  
  
```  
// C3181a.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181  
   Type ^pType2 = int::typeid;   // OK  
}  
```  
  
 下列範例會產生 C3181：  
  
```  
// C3181b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
int main() {  
   Type *pType1 = __typeof(int __gc*);   // C3181  
   Type *pType2 = __typeof(int*);   // OK  
}  
```