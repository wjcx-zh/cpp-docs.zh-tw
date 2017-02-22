---
title: "嚴重錯誤 C1305 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1305"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1305"
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 嚴重錯誤 C1305
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分析資料庫 'pgd\_file' 是供不同的架構使用  
  
 從另一個平台的 \/LTCG:PGINSTRUMENT 作業產生之.pgd 檔案已傳遞給 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)。  [特性指引最佳化](../../build/reference/profile-guided-optimizations.md) 皆可用於 x86平台 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 平台。  但是以一個平台的 \/LTCG:PGINSTRUMENT 作業產生的 .pgd 檔案對不同平台的 \/LTCG:PGOPTIMIZE 不是有效的輸入。  
  
 若要解除這項錯誤，只需傳遞用 \/LTCG:PGINSTRUMENT 建立的 .pgd 檔案給相同平台上的 \/LTCG:PGOPTIMIZE 即可。