---
title: "編譯器錯誤 C3610 | Microsoft Docs"
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
  - "C3610"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3610"
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3610
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'valuetype' : 在可以呼叫方法 'method' 前，實值型別必須為 'boxed'  
  
 按照預設，實值型別不是在 Managed 堆積上。  在從 .NET 執行階段類別 \(例如 `Object`\) 呼叫方法之前，必須先將實值型別移至 Managed 堆積上。  
  
 C3610 只能透過 **\/clr:oldSyntax** 取得。  
  
 下列範例會產生 C3610：  
  
```  
// C3610.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value class A {};  
  
int main() {  
   A a;  
   a.GetType(); // C3610  
  
   // OK  
   __box A* ovar = __box(a);  
   ovar->GetType();  
}  
```