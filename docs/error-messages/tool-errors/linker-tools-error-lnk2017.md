---
title: "連結器工具錯誤 LNK2017 | Microsoft Docs"
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
  - "LNK2017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2017"
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK2017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' 重新配置至 'segment' 不正確，沒有 \/LARGEADDRESSAWARE:NO  
  
 您嘗試用 32 位元位址建置一個 64 位元的映像。  若要達到這個目的，您必須：  
  
-   使用固定的載入位址。  
  
-   限制映像大小在 3 GB 以下。  
  
-   指定[\/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md)。