---
title: "編譯器錯誤 C3623 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3623"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3623"
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C3623
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable': Managed 或 WinRT 型別中不支援位元欄位  
  
 在 Managed 或 WinRT 類別中的變數上不允許使用位元欄位。  
  
 下列範例會產生 C3623：  
  
```  
// C3623.cpp  
// compile with: /clr  
using namespace System;  
ref class CMyClass {  
public:  
   int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass^ pMyClass = gcnew CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```  
  
 下列範例會產生 C3623：  
  
```  
// C3623_2.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__gc class CMyClass {  
   public:  
      int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass *pMyClass = new CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```