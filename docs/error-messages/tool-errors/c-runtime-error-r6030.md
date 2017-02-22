---
title: "C 執行階段錯誤 R6030 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6030"
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# C 執行階段錯誤 R6030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CRT 未初始化  
  
 如果您使用了 CRT，但未執行 CRT 的啟始程式碼，就會發生這個錯誤。  如果使用連結器參數 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 覆寫預設的開始位置 \(通常是 Console EXE 的 **mainCRTStartup**、**wmainCRTStartup**、Windows EXE 的 **WinMainCRTStartup** 或 **wWinMainCRTStartup**，或 DLL 的 **\_DllMainCRTStartup**\)，就有可能會得到這個錯誤。  除非在啟動時呼叫上述其中一個函式，否則將不會初始化 C 執行階段。