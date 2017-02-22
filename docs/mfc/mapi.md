---
title: "MAPI | Microsoft Docs"
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
  - "電子郵件, 啟用"
  - "針對郵件啟用應用程式"
  - "針對 MAPI 啟用應用程式"
  - "郵件, 啟用您的應用程式"
  - "MFC 中的 MAPI 支援"
  - "MAPI, MFC"
  - "傳訊, 用戶端應用程式"
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MAPI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明用戶端訊息應用程式開發人員的 Microsoft 訊息應用程式開發介面 \(MAPI\)。  MFC 提供支援 MAPI 的子集在類別 **CDocument** ，但不會封裝整個應用程式開發介面。  如需詳細資訊，請參閱 [在 MFC 的 MAPI 支援](../mfc/mapi-support-in-mfc.md)。  
  
 MAPI 是郵件允許和郵件感知應用程式用來建立，操作， 傳輸和儲存郵件的一組函式。  它在其儲存郵件的管理方面提供應用程式開發人員工具定義郵件訊息目的和內容並將這些彈性。  MAPI 也提供應用程式開發人員可以使用建立郵件允許和基本訊息系統的郵件感知應用程式無關的通用介面。  
  
 用戶端會呈現程序可以互動提供人類相互關聯式 Windows 架構訊息系統 \(WMS\)。  這種互動通常包含要求 MAPI 相容提供者的服務，例如訊息存放區和通訊錄。  
  
 如需 MAPI 的詳細資訊，請參閱 Microsoft 知識庫文件，在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 Win32 訊息 \(MAPI\) 的方針下 。  
  
## 本章節內容  
 [MFC 中的 MAPI 支援](../mfc/mapi-support-in-mfc.md)  
  
## 請參閱  
 [CDocument::OnFileSendMail](../Topic/CDocument::OnFileSendMail.md)   
 [CDocument::OnUpdateFileSendMail](../Topic/CDocument::OnUpdateFileSendMail.md)   
 [COleDocument::OnFileSendMail](../Topic/COleDocument::OnFileSendMail.md)