---
title: "剪貼簿：使用 Windows 剪貼簿 | Microsoft Docs"
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
  - "剪貼簿 [C++], 命令"
  - "剪貼簿 [C++], Windows 剪貼簿應用程式開發介面"
  - "剪貼簿命令"
  - "剪貼簿命令, 實作"
  - "命令 [C++], 實作編輯"
  - "剪下/複製及貼上命令處理函式"
  - "處理函式, 剪下/複製及貼上命令"
  - "Windows 剪貼簿 [C++]"
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剪貼簿：使用 Windows 剪貼簿
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題描述如何使用在 MFC 應用程式內的標準 Windows 剪貼簿應用程式開發介面。  
  
 對視窗的大部分應用程式支援剪下或複製資料到 Windows 剪貼簿和從剪貼簿中貼上資料。  剪貼簿資料格式在應用程式中變更。  架構支援有限數目的剪貼簿格式只能執行在有限數量類別。  您通常會實作剪貼簿相關命令—剪下，複製，然後貼上—在檢視的編輯功能表。  類別庫定義了這些命令的命令 ID: **ID\_EDIT\_CUT**和 **ID\_EDIT\_COPY**和 **ID\_EDIT\_PASTE**。  其訊息行提示也會定義。  
  
 [訊息和命令在 Framework](../mfc/messages-and-commands-in-the-framework.md) 說明如何藉由將功能表命令管理應用程式的功能表命令加入至處理函式。  只要您的應用程式未定義函式為剪貼簿在編輯功能表命令的處理常式，則會保持停用。  進行剪下和複製命令要撰寫處理常式函式，請實作在應用程式中的選取範圍。  要用於貼上命令要撰寫處理常式函式，請查詢剪貼簿查看是否在您的應用程式可以接受的格式的資料。  例如，若要複製命令，您可以類似下列來撰寫處理常式:  
  
 [!code-cpp[NVC_MFCListView#2](../mfc/codesnippet/CPP/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 剪下、複製和貼上在特定內容中命令才有意義。  只有在項目被選取時應該啟用剪下和複製命令，且在存在剪貼簿時貼上命令才會有效。  您可以藉由定義更新根據內容啟用或停用這些命令的處理常式函式提供這個行為。  如需詳細資訊，請參閱 [如何更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)。  
  
 MFC 程式庫為文字編輯提供剪貼簿支援以 `CEdit` 和 `CEditView` 類別。  OLE 類別也簡化了實作包含 OLE 項目的剪貼簿作業。  如需 OLE 類別的詳細資訊，請參閱 [剪貼簿:使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)。  
  
 實作其他編輯功能表命令，例如復原 \(**ID\_EDIT\_UNDO**\) 和重新作業 \(**ID\_EDIT\_REDO**\)，或保留給您。  如果您的應用程式不支援這些命令，使用 Visual C\+\+ 資源編輯器，您可以輕鬆地刪除它們從您的資源檔。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [複製和貼上資料](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## 請參閱  
 [剪貼簿](../mfc/clipboard.md)