---
title: "主動式文件內含項目 | Microsoft Docs"
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
  - "主動式文件容器 [C++], 關於主動式文件容器"
  - "主動式文件 [C++], 容器"
  - "容器 [C++], 主動式文件"
  - "MFC [C++], COM 支援"
  - "MFC COM [C++], 主動式文件內含項目"
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 主動式文件內含項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

現用文件內含項目是提供單一框架與文件一起使用，而不是強制您為每個資料型別建立和使用多個應用程式架構的技術。  它與基礎 OLE 技術不同 OLE 與內容只有單一組件可以是現用的複合文件中的內嵌物件一起使用。  現用文件內含項目，您可以在單一框架內啟動整份文件 \(也就是整個應用程式，包括關聯的功能表，工具列，依此類推\)。  
  
 現用文件內含技術原先開發以 Microsoft Office 可以實作 Office 文件夾。  不過，除了 Office 和 Office 相容應用程式之外，技術不夠彈性支援主動式文件容器刪除 Office 文件夾之外，而且可支援文件伺服器。  
  
 裝載現用文件的應用程式呼叫 [主動式文件容器](../mfc/active-document-containers.md)。  範例的這樣的容器是 Microsoft Office Binder 或 Microsoft Internet Explorer。  
  
 現用文件內含項目實作，一組 OLE 文件的副檔名， OLE 複合文件技術。  擴充功能已啟用可內嵌的其他介面，代表整份文件的就地物件而不是內嵌單一內容。  與 OLE 文件，主動式文件內含項目用於現用文件的顯示空間的使用中文件的使用者介面和管理功能的容器和伺服器。  
  
 [主動式文件伺服程式](../mfc/active-document-servers.md) 是一個應用程式 \(例如 Word、Excel、PowerPoint\) 對一或多個現用文件類別，其中每個物件支援在適當的容器允許物件啟動的擴充介面。  
  
 [現用文件](../mfc/active-documents.md) \(提供來自主動式文件伺服程式 \(例如 Word 或 Excel\) 基本上是內嵌為其他主動式文件容器內的物件之完整，一般文件。  不同於內嵌物件，現用文件有對其網頁的完整控制項，因此，應用程式的完整介面 \(與其所有基底命令和工具\) 可供使用者編輯這些項目。  
  
 現用文件最好是透過區別了解與標準 OLE 內嵌物件。  在 OLE 慣例之後，內嵌物件是在文件頁面中顯示其所屬的話，，且文件由 OLE 容器處理。  容器儲存內嵌物件的資料以文件的其餘部分。  不過，內嵌的物件會限制這些控制項會顯示的頁面。  
  
 主動式文件容器應用程式的使用者可以建立主動式文件 \(呼叫在 Office 文件夾區段\) 使用其偏好的應用程式 \(提供這些應用程式是啟用的主動式文件\)，因此，使用者可以處理產生的專案，在單一實體，可以唯一名稱，保存，列印，依此類推。  因此，網際網路瀏覽器的使用者可以將整個網路，以及檔案系統，做為單一檔案儲存實體能夠瀏覽該儲存的文件從一個位置。  
  
## 範例程式  
  
-   [MFCBIND](../top/visual-cpp-samples.md) 範例說明主動式文件容器應用程式的實作。  
  
## 請參閱  
 [MFC COM](../mfc/mfc-com.md)