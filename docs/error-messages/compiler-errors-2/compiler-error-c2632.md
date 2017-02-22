---
title: "編譯器錯誤 C2632 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2632"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2632"
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器錯誤 C2632
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1' 之後跟隨 'type2' 是不合法的  
  
 如果兩個型別規範之間遺漏了程式碼，可能就會發生這項錯誤。  
  
 下列範例會產生 C2632：  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 對 Visual Studio .NET 2003 的編譯器完成一致性處理後也可能會產生這項錯誤。  `bool` 現在是正確的型別。  在舊版中，`bool` 是 typedef，您可以用該名稱來建立識別項。  
  
 下列範例會產生 C2632：  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 若要解決這項錯誤，以使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效，請重新命名識別項。