---
title: "使用者介面物件和命令 ID | Microsoft Docs"
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
  - "命令處理, 使用者介面物件"
  - "命令 ID, 使用者介面物件"
  - "命令傳送, MFC"
  - "鍵盤快速鍵, 與 ID 產生關聯"
  - "功能表項目, 與 ID 產生關聯"
  - "MFC, 命令傳送"
  - "工具列控制項 [MFC], 命令 ID"
  - "使用者介面物件, 與 ID 產生關聯"
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者介面物件和命令 ID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

功能表項目、工具列按鈕和快速鍵是使用介面物件」能夠產生命令。  每一個使用者介面物件具有 ID.  建立自訂使用者介面物件與命令將相同 ID 的物件和命令。  如 [訊息](../mfc/messages.md)所說明，命令會實作為特殊資訊。  這個檢視在 Framework 命令」下面架構如何處理命令。  當使用者介面物件產生一命令，例如 `ID_EDIT_CLEAR_ALL`，一個應用程式的物件處理命令—在下面這個圖形，資料物件的 `OnEditClearAll` 函式會將文件的訊息對應呼叫。  
  
 ![Framework 中的命令](../mfc/media/vc385p1.png "vc385P1")  
Framework 中的命令  
  
 嘗試更新在 Framework 的命令」下面 MFC 如何更新使用者介面物件 \(例如功能表項目和工具列按鈕。  在工具列按鈕的情況下，才能在功能表下拉，或者在閒置迴圈期間， MFC 路由更新命令。  在下面這個圖形，資料物件呼叫它的更新命令處理常式，則為 `OnUpdateEditClearAll`，啟用或停用使用者介面物件。  
  
 ![Framework 中的命令更新](../mfc/media/vc385p2.png "vc385P2")  
Framework 中的命令更新  
  
## 請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)