---
title: "編譯器警告 (層級 4) C4032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4032"
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 4) C4032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

升級時型式參數 number 具有不同的型別  
  
 經過預設升級後，此參數型別與之前宣告中的型別不相容。  
  
 在 ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 中這是一項錯誤，在 Microsoft Extensions \(\/Ze\) 之下這是一項警告。  
  
## 範例  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```