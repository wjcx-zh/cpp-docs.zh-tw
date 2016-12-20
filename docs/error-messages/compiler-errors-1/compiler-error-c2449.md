---
title: "編譯器錯誤 C2449 | Microsoft Docs"
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
  - "C2449"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2449"
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2449
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

於檔案範圍找到 '{' \(遺漏函式標頭？\)  
  
 左括號出現在檔案範圍 \(File Scope\) 內。  
  
 這項錯誤可能是因為分號出現在函式標頭和函式定義的左括號之間而產生。  
  
 下列範例會產生 C2499：  
  
```  
// C2449.c  
// compile with: /c  
void __stdcall func(void) {}   // OK  
void __stdcall func(void);  // extra semicolon on this line  
{                         // C2449 detected here  
```