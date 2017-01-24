---
title: "專案建置警告 PRJ0041 | Microsoft Docs"
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
  - "PRJ0041"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0041"
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置警告 PRJ0041
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到檔案 'file' 所遺失的相依性 'dependency'，您的專案可能仍會建置，但在找到這個檔案前，都可能繼續顯示為過期。  
  
 檔案 \(例如資源檔或 .idl\/.odl 檔\) 含有專案系統無法解析的 include 陳述式。  
  
 由於專案系統不處理前置處理器陳述式 \(例如 \#if\)，因此違規的陳述式實際上可能不是組建的一部分。  
  
 若要解決這個警告，請刪除 .rc 檔中所有不必要的程式碼，或是加入適當名稱的預留位置檔案。