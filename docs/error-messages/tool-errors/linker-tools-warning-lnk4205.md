---
title: "連結器工具警告 LNK4205 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4205"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4205"
ms.assetid: d63b9d18-ef3c-4081-9d8d-93077dad13c2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具警告 LNK4205
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'filename' 遺漏目前參考模組的偵錯資訊；當做沒有偵錯資訊，連結物件  
  
 .pdb 檔的資訊過期。  連結器會繼續不使用偵錯資訊來連結目的檔。  您必須用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 選項重新編譯目的檔。