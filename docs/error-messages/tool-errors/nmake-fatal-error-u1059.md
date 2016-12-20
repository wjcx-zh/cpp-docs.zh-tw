---
title: "NMAKE 嚴重錯誤 U1059 | Microsoft Docs"
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
  - "U1059"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1059"
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1059
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 相依中遺漏 '}'  
  
 指定的相依搜尋路徑不正確。  可能是路徑中有空格，或省略了右大括號 \(**}**\)。  
  
 相依目錄的指定語法為  
  
 **{**   
 ***directories* }dependent**  
  
 其中的 `directories` 指定一或多個路徑，每個路徑之間以分號分隔 \(**;**\)。  不可以使用空格。  
  
 如果以巨集替代部分或所有的搜尋路徑，請確定巨集展開中沒有空格。