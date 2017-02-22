---
title: "C 執行階段錯誤 R6028 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6028"
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# C 執行階段錯誤 R6028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法初始化堆積  
  
 當作業系統無法為應用程式建立記憶體集區時，便會發生這個錯誤。  特別是，C 執行階段 \(CRT\) 會呼叫 Win32 函式 `HeapCreate`，該函式會傳回表示錯誤的 NULL。  
  
 如果在應用程式啟動時發生這個錯誤，系統可能因為載入了不良的驅動程式而無法滿足堆積要求。  請查看 Windows Update 或硬體廠商的網站是否有更新的驅動程式。