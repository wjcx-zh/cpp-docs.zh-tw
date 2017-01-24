---
title: "NMAKE 警告 U4011 | Microsoft Docs"
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
  - "U4011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4011"
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 警告 U4011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'target' : 無法取得所有相依性; 未建置目標  
  
 給定目標的相依不存在或已過期，且更新此相依的命令傳回非零的結束代碼。  \/K 選項告訴 NMAKE 繼續處理建置中其他不相關的部分，並在 NMAKE 作業階段完成後發出結束代碼 1。  
  
 在發出這個警告之前，每一個建立或更新失敗的相依都會發出 [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) 警告。