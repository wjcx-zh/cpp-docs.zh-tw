---
title: "Makefile 中的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令, Makefile"
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Makefile 中的命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果相依性已過時，描述區塊或推斷規則就會指定要執行的命令區塊。  NMAKE 會先顯示每個命令之後才執行，除非使用 \/S、**.SILENT**、**\!CMDSWITCHES**，或 @。  如果描述區塊後面沒有跟隨著命令區塊，NMAKE 就會尋找相符的推斷規則。  
  
 命令區塊包含一個或多個命令，每個命令都位於本身那一行。  在相依性或規則與命令區塊之間，不能出現空白行。  但是，可以出現只包含空格或定位字元的行，此行會被解譯為 null 命令，而不會發生錯誤。  在命令列之間允許出現空白行。  
  
 命令列以一個或多個空格或定位字元開頭。  反斜線 \(\\\) 後面跟隨新行字元會被解譯為命令中的空挌，請在行的結尾處使用反斜線，以便命令由下一行繼續。  如果任何其他字元 \(包括空格或定位字元\) 跟隨在反斜線之後，NMAKE 會將反斜線解譯為常值。  
  
 無論命令區塊是否緊接其後，由分號 \(;\) 開頭的命令都可以出現在相依性行或推斷規則中：  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [命令修飾詞](../build/command-modifiers.md)  
  
 [檔名部分語法](../build/filename-parts-syntax.md)  
  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)  
  
## 請參閱  
 [NMAKE 參考](../build/nmake-reference.md)