---
title: "編譯器錯誤 C3800 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3800"
ms.assetid: c653240a-b6db-4437-8d65-fa58f0e6fcf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration' : 屬性與事件不可以混合  
  
 您不能將建構同時宣告為屬性和事件。  
  
 C3800 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C3800：  
  
```  
// C3800.cpp  
// compile with: /clr:oldSyntax  
#using "mscorlib.dll"  
  
__delegate void MyDel();  
public __gc struct S  
{  
   __property __event void set_E(MyDel*)  
   {  
   }   // C3800  
};  
  
int main()  
{  
}  
```