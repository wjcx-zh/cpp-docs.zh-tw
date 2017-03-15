---
title: "BSCMAKE 命令檔 (回應檔) | Microsoft Docs"
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
  - "BSCMAKE, 命令檔"
  - "BSCMAKE, 回應檔"
  - "命令檔"
  - "命令檔, BSCMAKE"
  - "回應檔"
  - "回應檔, BSCMAKE"
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# BSCMAKE 命令檔 (回應檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以在命令檔 \(Command File\) 中提供部分或完整的命令列輸入。  並以下列語法指定命令檔：  
  
```  
BSCMAKE @filename  
```  
  
 只允許有一個命令檔。  您可以用 *filename* 指定路徑。  並在 *filename* 前加上 @ 符號。  BSCMAKE 不會假設副檔名。  您可以於命令列上在 *filename* 之後指定其他的 *sbrfile*。  命令檔是一個包含 BSCMAKE 輸入的文字檔，內容順序與在命令列中指定的順序相同。  請以一或多個空格、Tab 字元或新行字元 \(Newline Character\) 來分隔命令列引數。  
  
 下列命令會使用命令檔呼叫 BSCMAKE：  
  
```  
BSCMAKE @prog1.txt  
```  
  
 下列是範例命令檔：  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## 請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)