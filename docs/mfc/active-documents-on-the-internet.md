---
title: "網際網路上的主動式文件 | Microsoft Docs"
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
  - "主動式文件 [C++], 建立"
  - "主動式文件 [C++], 程式設計步驟"
  - "主動式文件 [C++], 使用應用程式精靈"
  - "應用程式精靈 [C++]"
  - "應用程式精靈 [C++], 主動式文件"
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 網際網路上的主動式文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

主動式文件提供擴充功能給傳統的內嵌物件。  主動式文件可能為多頁並顯示於整個工作區中。  它們與傳統功能表協調，並可就地編輯以及在伺服器應用程式中開啟的視窗。  主動式文件是全框且永遠就地啟動，而不是顯示為由串聯框線包圍的小矩形。  
  
 主動式文件可在類似 Microsoft Office Binder 的容器檢視，這提供建立複合文件組成如 Excel ，Word 中不同的資料型別和您的自訂文件類型，每一個可在完整框編輯。  主動式文件也可以在瀏覽器顯示像是 Microsoft Internet Explorer，它是主動式文件容器。  
  
 **主動式文件的優點包括:**  
  
-   文件可以在完整框檢視，在整個用戶端視窗。  
  
-   文件可在不同的應用程式視窗中開啟。  
  
     若要開啟的文件，協助工具應用程式在用戶端必須存在或個別下載，應用程式才能執行。  撰寫檢視器以提供部分功能 \(Word、Excel 和 PowerPoint 為其提供文件檢視器\)。  應用程式的完整版本可以提供最大的編輯支援。  
  
-   文件永遠是就地啟動。  
  
-   從容器叫用的命令可以傳送至您的文件。  
  
-   文件可在 Web 瀏覽器中檢視。  這提供在文件和其他 Web 網頁之間的緊密整合。  
  
     使用者可以瀏覽 HTML 網頁，然後 Excel 報表，然後您使用 MFC 支援主動式文件撰寫的文件。  因為瀏覽器完美地在 HTML 網頁、Excel 和您的應用程式資料的功能表和檢視之間切換，可讓使用者使用熟悉的 Web 介面巡覽。  
  
-   所有應用程式在     常見的框架中顯示。  
  
## 主動式文件的要求  
 下表所列的介面中包含對內嵌於伺服器上所需的介面和數個新介面下特有的主動式文件。  MFC 為大部分 [COleServerDoc](../mfc/reference/coleserverdoc-class.md) 類別的這些介面提供預設實作。  
  
|這文件…|會實作這些介面|  
|----------|-------------|  
|使用複合檔案做為它的儲存機制。|`IPersistStorage`.|  
|支援主動式文件的基礎內嵌功能，包括從文件建立。|`IPersistFile`、`IOleObject` 和 `IDataObject`。|  
|支援就地啟動|`IOleInPlaceObject` 和 `IOleInPlaceActiveObject` \(使用容器的 `IOleInPlaceSite` 和 **IOleInPlaceFrame** 介面\)。|  
|支援包含這些新介面的主動式文件擴充功能。  有些介面是選擇性的。|`IOleDocument`、`IOleDocumentView`、`IOleCommandTarget`和`IPrint`。|  
  
 MFC 提供擴充現有的內嵌伺服器支援主動式文件。  
  
## 對新應用程式加入主動式文件支援  
 建立主動式文件支援的新應用程式:在 MFC 應用程式精靈， **複合式文件支援** 頁面，在「選擇複合文件支援」下選取 **Full\-server** 或 **Container\/Full\-server**，以及在「選取其他選項」下為 **主動式文件伺服器**選取核取方塊。  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> 轉換現有 MFC 同處理序伺服程式到主動式文件伺服程式  
 如果您的應用程式以 Visual C\+\+ 4.2 之前的版本建立且已經是處理序伺服程式，您可以對下列類別的變更加入主動式文件支援:  
  
|類別類型|先前衍生自|變更衍生自|  
|----------|-----------|-----------|  
|就地框架|`COleIPFrameWnd`|**COleDocIPFrameWnd**|  
|項目|`COleServerItem`|`CDocObjectServerItem`|  
  
 您也需變更資訊如何在登錄中輸入，並進行其他變更。  如果您的應用程式目前不支援 COM 元件，您可以執行應用程式精靈與您的現有應用程式的 COM 元件和特定的程式碼作整合以加入伺服器支援。  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)