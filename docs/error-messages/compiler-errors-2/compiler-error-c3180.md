---
title: "編譯器錯誤 C3180 | Microsoft Docs"
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
  - "C3180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3180"
ms.assetid: 5281f583-7df7-418a-8507-d4da67ed6572
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3180
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type name' : 名稱超過中繼資料 'limit' 個字元的限制  
  
 編譯器截斷中繼資料 \(Metadata\) 中 Managed 型別的名稱。  截斷會造成無法透過 `#using` 指示詞 \(或其他語言中相當的指示詞\) 使用型別。  
  
 型別名稱的限制包含任何命名空間限制。