---
title: "NMAKE 嚴重錯誤 U1064 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1064"
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 嚴重錯誤 U1064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到 MAKEFILE，且沒有指定目標  
  
 NMAKE 命令列沒有指定 Makefile 或目標，目前目錄中也沒有包含名為 MAKEFILE 的檔案。  
  
 NMAKE 必須要有 Makefile 或命令列目標 \(或兩者\)。  若要為 NMAKE 提供 Makefile，可以指定 \/F 選項或在目前目錄中放置名為 MAKEFILE 的檔案。  沒有提供 Makefile 時，NMAKE 可以利用推斷規則建立命令列目標。