---
title: "命令列警告 D9027 | Microsoft Docs"
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
  - "D9027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9027"
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令列警告 D9027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已忽略原始程式檔 '\<filename\>'  
  
 CL.exe 忽略了輸入的原始程式檔 \(Source File\)。  
  
 可能是因為在用了 \/c 選項的命令列上，\/Fo 選項與輸出檔名之間有空格而產生這項警告。  例如：  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 因為 \/Fo 和 `output.obj,` 之間有空格，所以 CL.exe 將 `output.obj` 視為輸入檔的檔名。  若要修正這項問題，請將空格移除：  
  
```  
cl /c /Fooutput.obj input.c   
```