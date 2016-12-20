---
title: "命令列警告 D9026 | Microsoft Docs"
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
  - "D9026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9026"
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令列警告 D9026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

選項套用到整個命令列  
  
 在指定檔名之後，有選項在命令上被指定。  則此選項會被套用在它前面的檔案上。  
  
 例如，在下列命令中  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 檔案 VERDI.c 將使用 \/G5 選項來編譯，而非預設的 \/G4 選項。  
  
 此行為與之前的版本不同，之前的版本只套用指定檔案名稱之前的選項，使得 VERDI.c 會以 \/G4 選項來編譯而 PUCCINI.c 會以 \/G5 選項來編譯。