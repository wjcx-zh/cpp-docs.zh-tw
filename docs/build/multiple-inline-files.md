---
title: "多重內嵌檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內嵌檔, 多重 NMAKE"
  - "多重內嵌檔"
  - "NMAKE 程式, 內嵌檔"
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 多重內嵌檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令能建立一個以上的內嵌檔。  
  
## 語法  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## 備註  
 為每個檔案指定一或多行內嵌文字，文字後跟隨包含分隔符號的結尾行。  從第一個檔案分隔行的下一行，開始第二個檔案的文字。  
  
## 請參閱  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)