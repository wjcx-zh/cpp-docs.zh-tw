---
title: "NMAKE 嚴重錯誤 U1045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1045"
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# NMAKE 嚴重錯誤 U1045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

繁衍失敗：訊息  
  
 NMAKE 所呼叫的程式或命令因指定原因而失敗。  當 NMAKE 呼叫另一個程式 \(例如，編譯器或連結器\) 時，呼叫可能會失敗，或是被呼叫的程式可能會傳回錯誤。  此訊息用來報告錯誤。  
  
 如果要修正這個問題，請先判斷錯誤的原因。  您可以在命令列上使用 NMAKE [\/N](../../build/nmake-options.md) 選項所報告的命令來確認環境設定，並重複執行 NMAKE 所執行的動作。