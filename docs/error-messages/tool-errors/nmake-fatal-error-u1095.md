---
title: "NMAKE 嚴重錯誤 U1095 | Microsoft Docs"
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
  - "U1095"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1095"
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1095
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

展開的命令列 'commandline' 太長  
  
 巨集展開後，給定的命令列超過作業系統的命令列長度限制。  
  
 MS\-DOS 允許命令列最長 128 個字元。  
  
 如果命令是可以接受檔案的命令列輸入的程式，修改命令並由磁碟中的檔案或內嵌檔提供輸入。  例如，LINK 和 LIB 可以接受來自回應檔 \(Response File\) 的輸入。