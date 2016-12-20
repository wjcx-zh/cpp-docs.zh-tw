---
title: "NMAKE 嚴重錯誤 U1073 | Microsoft Docs"
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
  - "U1073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1073"
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不知如何建立 'targetname'  
  
 指定的目標不存在，也沒有要執行的命令或要套用的推斷規則。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  檢查目標名稱的拼字是否正確。  
  
2.  如果 *targetname* 是虛擬目標 \(Pseudotarget\)，請在另一個描述區塊中將它指定為目標。  
  
3.  如果 *targetname* 是巨集引動過程，請確定它不會展開成 Null 字串。