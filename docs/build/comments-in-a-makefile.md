---
title: "Makefile 中的註解 | Microsoft Docs"
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
  - "Makefile, 註解"
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Makefile 中的註解
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在註解之前必須有數字正負號 \(\#\)。  NMAKE 會忽略從數字正負號到下一個新行字元之間的文字，  例如：  
  
```  
# Comment on line by itself  
OPTIONS = /MAP  # Comment on macro definition line  
  
all.exe : one.obj two.obj  # Comment on dependency line  
    link one.obj two.obj  
# Comment in commands block  
#   copy *.obj \objects  # Command turned into comment  
    copy one.exe \release  
  
.obj.exe:  # Comment on inference rule line  
    link $<  
  
my.exe : my.obj ; link my.obj  # Err: cannot comment this  
 # Error: # must be the first character  
.obj.exe: ; link $<  # Error: cannot comment this  
```  
  
 若要指定常值數字正負號，前面必須要有插入號 \(**^**\)，如下所示：  
  
```  
DEF = ^#define  #Macro for a C preprocessing directive  
```  
  
## 請參閱  
 [Makefile 內容](../build/contents-of-a-makefile.md)