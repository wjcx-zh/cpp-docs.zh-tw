---
title: "萬用字元展開 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_setargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setargv 函式"
  - "星號萬用字元"
  - "命令列, 處理引數"
  - "命令列, 萬用字元"
  - "命令列萬用字元"
  - "問號, 萬用字元"
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 萬用字元展開
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 您可以在命令列上使用問號 \(?\) 和星號 \(\*\) 等萬用字元來指定檔案名稱和路徑引數。  
  
 命令列引數由呼叫 **\_setargv** \(或寬字元環境中的 **\_wsetargv**\) 的常式處理，預設不會將 `argv` 字串陣列中的萬用字元展開為個別的字串。  如需啟用萬用字元展開的詳細資訊，請參閱[展開萬用字元引數](../c-language/expanding-wildcard-arguments.md)。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)