---
title: "資源編譯器嚴重錯誤 RW1025 | Microsoft Docs"
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
  - "RW1025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW1025"
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資源編譯器嚴重錯誤 RW1025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆積記憶體嚴重不足  
  
 請檢查可能佔據太多空間的常駐記憶體軟體。  請使用 CHKDSK 程式來找出您還有多少記憶體空間。  
  
 若您正在建立較大的資源檔，請將資源指令碼分割為兩個檔案。  在建立兩個 .res 檔之後，再使用下列的 MS\-DOS 命令列連結兩個檔案：  
  
```  
copy first.res /b + second.res /b full.res  
```