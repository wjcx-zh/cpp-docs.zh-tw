---
title: "建立內嵌檔文字 | Microsoft Docs"
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
  - "內嵌檔, 建立文字"
  - "NMAKE 程式, 內嵌檔"
  - "文字, 內嵌檔"
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建立內嵌檔文字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內嵌 \(Inline\) 檔是暫存性的或永久性的。  
  
## 語法  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## 備註  
 在命令之後的第一行指定 *inlinetext*。  在不同行的開頭使用雙角括弧 \(\<\<\) 標記結尾。  檔案包含在分隔括號之前的所有 *inlinetext*。  *inlinetext* 可以有巨集展開或替代，但不能有指示詞或 Makefile 註解。  將空格、定位字元和新行字元 \(Newline Character\) 視為常值。  
  
 在工作階段期間有暫存檔，可以供其他命令重複使用。  在右邊的角括弧之後指定 **KEEP**，以便在 NMAKE 工作階段後保留檔案，未命名的檔案會以產生的檔名保留在磁碟中。  為暫存檔指定 **NOKEEP** 或完全不指定。  **KEEP** 和 **NOKEEP** 不區分大小寫。  
  
## 請參閱  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)