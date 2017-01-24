---
title: "在內嵌組譯碼中呼叫 C++ 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 呼叫函式"
  - "函式呼叫, C++ 函式"
  - "函式呼叫, 在內嵌組譯碼中"
  - "函式 [C++], 在內嵌組譯碼中呼叫"
  - "內嵌組譯碼, 呼叫函式"
  - "Visual C++, 函式"
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在內嵌組譯碼中呼叫 C++ 函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 `__asm` 區塊只能呼叫未多載的全域 C\+\+ 函式。  如果您呼叫多載的全域 C\+\+ 函式或 C \+\+ 成員函式，編譯器會發出錯誤。  
  
 您也可以呼叫所有以 **extern "C"** 連結宣告的函式。  由於所有的標準標頭檔都會宣告程式庫函式擁有 **extern "C"** 連結，因此這樣就可以讓 C\+\+ 程式內的 `__asm` 區塊呼叫 C 程式庫函式。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)