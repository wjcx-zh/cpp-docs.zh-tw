---
title: "視窗程序進入點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "進入點, 視窗程序"
  - "MFC, 管理狀態資料"
  - "狀態管理, 視窗程序"
  - "視窗程序進入點"
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 視窗程序進入點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了保護 MFC 視窗程序，模組靜態連結至具有特殊視窗程序的實做。  當模組與 MFC 連結時，連接就會自動發生。  這個視窗程序使用 `AFX_MANAGE_STATE` 巨集以適當地設定有效的模組狀態，然後呼叫 **AfxWndProc**，它委派至衍生自適當的 `CWnd` 物件的適當的 `WindowProc` 成員函式。  
  
## 請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)