---
title: "動態物件建立 | Microsoft Docs"
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
helpviewer_keywords: 
  - "CObject 類別, 動態物件建立"
  - "動態物件建立"
  - "建立物件, 在執行階段動態"
  - "物件 [C++], 在執行階段動態建立"
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 動態物件建立
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何動態的在執行階段建立物件。  程序會使用執行階段類別資訊，如 [存取的執行階段類別資訊](../mfc/accessing-run-time-class-information.md) 中所述。  
  
#### 若要在執行階段類別動態地建立指定的物件  
  
1.  使用 `CRuntimeClass` 的 `CreateObject` 函式，使用下列程式碼動態建立物件。  請注意在失敗時， `CreateObject` 會傳回 **NULL** 而不會引發例外狀況：  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/CPP/dynamic-object-creation_1.cpp)]  
  
## 請參閱  
 [使用 CObject](../mfc/using-cobject.md)