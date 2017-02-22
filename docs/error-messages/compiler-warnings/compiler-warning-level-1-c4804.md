---
title: "編譯器警告 (層級 1) C4804 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4804"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4804"
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 1) C4804
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operation' : 作業中不安全的使用型別 'bool'  
  
 當您以未預期的方法使用 `bool` 變數或值時，就會產生此警告。  例如，如果您使用負數一元 \(Unary\) 運算子 \(**\-**\) 或補數 \(Complement\) 運算子 \(`~`\) 之類的運算子時，就會產生 C4804。  編譯器會評估運算式。  
  
## 範例  
 下列範例會產生 C4804：  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```