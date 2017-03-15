---
title: "NMAKE 警告 U4004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U4004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4004"
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 警告 U4004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

目標 'targetname' 有太多規則  
  
 使用單冒號 \(**:**\) 做為分隔符號的給定目標指定了一個以上的描述區塊。  NMAKE 只會執行第一個描述區塊中的命令，並忽略後面的區塊。  
  
 若要在多個相依性中指定同一個目標，請在每一個相依性列中使用雙冒號 \(`::`\) 做為分隔符號。