---
title: "2.6.1 master Construct | Microsoft Docs"
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
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.1 master Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**主要**指示詞會識別指定的結構化的區塊，小組的主執行緒所執行的建構。  語法**主要**指示詞時，如下所示：  
  
```  
#pragma omp master new-line  
   structured-block  
```  
  
 在小組中的其他執行緒不會執行相關聯的結構化的區塊。  沒有暗示的屏障進入或離開主機的建構上。