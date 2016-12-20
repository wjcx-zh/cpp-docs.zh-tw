---
title: "CVTRES 嚴重錯誤 CVT1100 | Microsoft Docs"
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
  - "CVT1100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CVT1100"
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CVTRES 嚴重錯誤 CVT1100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重複的資源 \-\- type:type、name:name、 language:language、flags:flags、size:size  
  
 給定的資源被指定了一次以上。  
  
 如果連結器 \(Linker\) 建立了型別程式庫，而您未指定 [\/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md)，且您專案中的資源已經使用 1，就會得到這個錯誤。  在這種情形下，請指定 \/TLBID 並指定其他數字 \(最大值為 65535\)。