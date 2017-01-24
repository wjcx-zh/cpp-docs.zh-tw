---
title: "編譯器警告 (層級 1) C4650 | Microsoft Docs"
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
  - "C4650"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4650"
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4650
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵錯資訊不在先行編譯標頭檔中；只能使用來自標頭的全域符號  
  
 先行編譯標頭檔沒有以 Microsoft 符號偵錯資訊 \(Symbolic Debugging Information\) 編譯。  
  
 連結時產生的可執行檔或動態連結程式庫檔不會包括先行編譯標頭中的區域符號偵錯資訊。  
  
 以 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 命令列選項重新編譯先行標頭檔可避免此警告。