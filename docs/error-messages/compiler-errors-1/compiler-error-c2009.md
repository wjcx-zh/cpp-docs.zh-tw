---
title: "編譯器錯誤 C2009 | Microsoft Docs"
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
  - "C2009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2009"
ms.assetid: fe9d94ed-20a5-4d83-b9c4-60ee69d2f30a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

巨集型式 'identifier' 重複使用  
  
 某巨集定義的型式參數清單 \(Formal Parameter List\) 使用該識別項超過一次。  巨集參數清單內的識別項必須是唯一的。  
  
## 範例  
 下列範例會產生 C2009：  
  
```  
// C2009.cpp  
#include <stdio.h>  
  
#define macro1(a,a) (a*a)   // C2009  
  
int main()   
{  
    printf_s("%d\n", macro1(2));  
}  
```  
  
## 範例  
 可能的解決方案：  
  
```  
// C2009b.cpp  
#include <stdio.h>  
  
#define macro2(a)   (a*a)   
#define macro3(a,b) (a*b)  
  
int main()   
{  
    printf_s("%d\n", macro2(2));  
    printf_s("%d\n", macro3(2,4));  
}  
```