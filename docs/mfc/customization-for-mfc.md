---
title: "MFC 自訂 | Microsoft Docs"
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
  - "自訂, MFC 擴充功能"
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
caps.latest.revision: 21
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 自訂
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題提供自訂 MFC 應用程式的秘訣。  
  
## 一般自訂  
 您可以儲存和載入您的應用程式狀態至登錄（registry）。  當您啟用這個選項，您的應用程式會從登錄載入其初始狀態。  如果您變更應用程式的初始停駐配置，您必須清除應用程式的登錄資料。  否則，登錄內的資料將會覆寫您對初始設定的所有變更。  
  
## 類別專屬的自訂  
 其他自訂技巧可以在下列主題中找到：  
  
-   [CBasePane Class](../mfc/reference/cbasepane-class.md)  
  
-   [CDockablePane Class](../mfc/reference/cdockablepane-class.md)  
  
-   [CDockingManager Class](../mfc/reference/cdockingmanager-class.md)  
  
-   [CMFCBaseTabCtrl Class](../mfc/reference/cmfcbasetabctrl-class.md)  
  
## 其他自訂技巧  
 [鍵盤和滑鼠自訂](../mfc/keyboard-and-mouse-customization.md)  
  
 [使用者定義類型](../mfc/user-defined-tools.md)  
  
## 請參閱  
 [MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)   
 [自訂的安全性影響](../mfc/security-implications-of-customization.md)