---
title: "MFC 使用的回呼函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.functions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "回呼函式"
  - "回呼函式, MFC"
  - "函式 [C++], 回呼"
  - "MFC, 回呼函式"
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 使用的回呼函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

三個回呼函式會出現在 MFC 程式庫。  傳遞給 [CDC::EnumObjects](../Topic/CDC::EnumObjects.md)回呼函式， [CDC::GrayString](../Topic/CDC::GrayString.md)和 [CDC::SetAbortProc](../Topic/CDC::SetAbortProc.md) 的說明遵循這個主題。  如需回呼函式的一般使用方式，請參閱下列成員函式的 \< 備註 \> 一節。  請注意任何回呼函式必須在傳回之前截取 MFC 例外加入到 Windows，，因為例外狀況無法跨界限回呼會擲回。  如需例外狀況的詳細資訊，請參閱本文件的 [例外狀況。](../../mfc/exception-handling-in-mfc.md)。  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)