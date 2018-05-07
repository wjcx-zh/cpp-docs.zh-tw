---
title: 在網際網路上的主動式文件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], creating
- application wizards [MFC], active documents
- active documents [MFC], programming steps
- application wizards [MFC]
- active documents [MFC], using application wizards
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43bb54f36f57702d43cf065604641124e38ed053
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="active-documents-on-the-internet"></a>網際網路上的主動式文件
主動式文件提供傳統的內嵌物件的擴充功能。 主動式文件可能會多頁，而且會顯示整個工作區中。 它們執行傳統功能表交涉，且可以就地與伺服器應用程式中開啟的視窗中編輯。 而不是顯示為以陰影的框線括住的小矩形，主動式文件會是完整的畫面格和一律就地啟用作用中。  
  
 主動式文件都可提供方法來建立複合文件組成不同的文件類型，例如 Excel、 Word、 Microsoft Office Binder 如容器中，您的自訂文件類型，其中每一個都可以編輯完整的畫面格。 主動式文件也可以顯示在瀏覽器，例如 Microsoft Internet Explorer，是使用中文件的容器。  
  
 **主動式文件的優點包括：**  
  
-   文件可以檢視完整的畫面格，將整個用戶端視窗中。  
  
-   您可以在個別的應用程式視窗中開啟文件。  
  
     若要開啟 文件，協助應用程式必須存在於用戶端，或應用程式才能執行個別下載。 檢視器可能會寫入提供有限的功能 （Word、 PowerPoint 和 Excel 提供其文件檢視器）。 應用程式的完整版本可編輯的完整支援。  
  
-   文件永遠是就地啟用作用中。  
  
-   從容器中叫用的功能表命令可以路由傳送至您的文件。  
  
-   在 Web 瀏覽器中，您可以檢視文件。 這會提供您的文件和其他網頁之間的緊密整合。  
  
     使用者可以瀏覽 HTML 網頁，然後的 Excel 試算表，，，然後您撰寫使用 MFC 的文件支援主動式文件。 使用者可以瀏覽使用熟悉的 Web 介面，以瀏覽器緊密之間切換的功能表和檢視的 HTML 網頁、 Excel 和應用程式的文件。  
  
-   所有應用程式會顯示在一般的框架。  
  
## <a name="requirements-for-active-documents"></a>主動式文件的需求  
 下表中列出的介面包含已內嵌伺服器所需的介面和主動式文件的特定幾個新介面。 MFC 提供了大部分的這些介面的預設實作[COleServerDoc](../mfc/reference/coleserverdoc-class.md)類別。  
  
|文件...|實作這些介面|  
|-------------------------|---------------------------------|  
|使用複合檔案做為其儲存機制。|`IPersistStorage`.|  
|支援主動式文件，包括從檔案建立的基礎內嵌功能。|`IPersistFile`、`IOleObject` 和 `IDataObject`。|  
|支援就地啟用。|`IOleInPlaceObject` 和`IOleInPlaceActiveObject`(使用容器的`IOleInPlaceSite`和**IOleInPlaceFrame**介面)。|  
|支援包含這些新介面的使用中文件副檔名。 某些介面是選擇性的。|`IOleDocument`、`IOleDocumentView`、`IOleCommandTarget`和`IPrint`。|  
  
 MFC 提供支援，以擴充現有內嵌的伺服器支援主動式文件。  
  
## <a name="add-active-document-support-to-a-new-application"></a>主動式文件支援加入新的應用程式  
 若要建立新的應用程式與主動式文件支援： MFC 應用程式精靈 」 中，於**複合文件支援**頁面上，「 選取的複合文件支援 」 底下選擇**全伺服器**或**容器/全伺服器**，然後在 [選取其他選項] 下選取核取方塊**主動式文件伺服**。  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> 將現有的 MFC 同處理序伺服器轉換成使用中文件伺服器  
 如果您的應用程式建立 Visual c + + 4.2 版之前的版本，並且已經在處理序伺服器，您可以藉由變更下列類別加入使用中文件支援：  
  
|類別型別|先前，衍生自|若要從衍生的變更|  
|----------------|---------------------------|---------------------------|  
|就地編輯框架|`COleIPFrameWnd`|**COleDocIPFrameWnd**|  
|項目|`COleServerItem`|`CDocObjectServerItem`|  
  
 您也會變更在登錄中，輸入資訊的方式，並進行數個其他變更。 如果您的應用程式目前不有任何 COM 元件支援，您可以新增以執行應用程式精靈，並整合與您現有的應用程式的 COM 元件專屬的程式碼的伺服器支援。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)

