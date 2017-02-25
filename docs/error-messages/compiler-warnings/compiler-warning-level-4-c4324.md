---
title: "編譯器警告 (層級 4) C4324 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4324"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4324"
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器警告 (層級 4) C4324
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'struct\_name': 由於 \_\_declspec\(align\(\)\)，已填補結構  
  
 結構的末端加入填補，因為您指定了一個 [\_\_declspec\(align\)](../../cpp/align-cpp.md) 值。  
  
 例如，下列程式碼會產生 C4324：  
  
```  
// C4324.cpp  
// compile with: /W4  
struct __declspec(align(32)) A  
{  
   char a;  
};   // C4324  
  
int main()  
{  
}  
```