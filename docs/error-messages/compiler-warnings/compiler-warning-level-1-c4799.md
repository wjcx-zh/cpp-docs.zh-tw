---
title: "編譯器警告 (層級 1) C4799 | Microsoft Docs"
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
  - "C4799"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4799"
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4799
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函式 'function' 結尾沒有 EMMS  
  
 函式至少有一個 MMX 指令，但沒有 EMMS 指令。  使用多媒體指令時，也應該使用 EMMS 指令來清除 MMX 程式碼結尾的多媒體標記文字。  如需關於 EMMS 指令的詳細資訊，請參閱[何時使用 EMMS 的規定](http://msdn.microsoft.com/zh-tw/a0c3b1e4-01a4-419c-a58f-ff1e97dea7d3)。  
  
 當使用 ivec.h 時可能會產生 C4799，表示程式碼在返回前未正確執行 EMMS 指令。  這是這些標頭的假警告。  您可以在 ivec.h 中定義 \_SILENCE\_IVEC\_C4799 以關閉它們。  然而，請小心這麼做也會使編譯器不再對此類型提供正確的警告。  
  
 如需相關資訊，請參閱 [Intel MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。