---
title: "NMAKE 警告 U4007 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U4007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4007"
ms.assetid: 61ec0417-6961-43c1-ade8-f9d6e93289e9
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# NMAKE 警告 U4007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔名 'filename' 太長; 刪減為 DOS 8.3 格式  
  
 給定檔案的主檔名 \(Base Name\) 超過八個字元，或是副檔名超過三個字元。  NMAKE 將名稱刪減為八個字元的主檔名及三個字元的副檔名。  
  
 如果您的檔案系統支援長檔名，將檔名置於雙引號 \(**"**\) 之間。