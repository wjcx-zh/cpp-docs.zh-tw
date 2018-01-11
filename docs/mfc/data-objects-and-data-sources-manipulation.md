---
title: "資料物件和資料來源： 操作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40bd83b2e472ff1b1e5d277c27a801b0750fb160
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-objects-and-data-sources-manipulation"></a>資料物件和資料來源：管理
建立資料物件或資料來源之後，您可以執行的數字的資料，例如插入和移除資料，列舉資料的格式，以及其他更多資訊的一般作業。 本文說明完成最常見的作業所需的技巧。 主題包括：  
  
-   [將資料插入資料來源](#_core_inserting_data_into_a_data_source)  
  
-   [判斷資料物件中可用的格式](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [從資料物件擷取資料](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a>將資料插入資料來源  
 資料插入至資料來源的方式取決於資料是否立即提供或依需求，並以何種媒體提供它。 可能值如下所示。  
  
### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供資料 （立即轉譯）  
  
-   呼叫`COleDataSource::CacheGlobalData`重複為您提供資料的每個剪貼簿格式。 將剪貼簿格式，要使用包含資料的記憶體的控制代碼，並選擇性地**FORMATETC**結構描述資料。  
  
     -或-  
  
-   如果您想要直接使用**STGMEDIUM**結構，您呼叫`COleDataSource::CacheData`而不是`COleDataSource::CacheGlobalData`上述選項中。  
  
### <a name="supplying-data-on-demand-delayed-rendering"></a>提供的資料 （延遲轉譯）  
 這是進階的主題。  
  
-   呼叫`COleDataSource::DelayRenderData`重複為您提供資料的每個剪貼簿格式。 將剪貼簿格式來傳遞，並選擇性地**FORMATETC**結構描述資料。 當要求資料時，架構會呼叫`COleDataSource::OnRenderData`，您必須覆寫。  
  
     -或-  
  
-   如果您使用`CFile`提供資料的物件呼叫`COleDataSource::DelayRenderFileData`而不是`COleDataSource::DelayRenderData`中前一個選項。 當要求資料時，架構會呼叫`COleDataSource::OnRenderFileData`，您必須覆寫。  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>判斷資料物件中可用的格式  
 應用程式可讓使用者貼上資料之前，它必須知道它可以處理在剪貼簿上是否有格式。 若要這樣做，您的應用程式應該執行下列動作：  
  
1.  建立`COleDataObject`物件和**FORMATETC**結構。  
  
2.  呼叫資料物件的`AttachClipboard`成員函式來將資料物件與剪貼簿上的資料產生關聯。  
  
3.  執行下列任一步驟：  
  
    -   呼叫資料物件的`IsDataAvailable`需要成員函式，如果有一個或兩個格式。 將此時間在剪貼簿上的資料，支援更多的格式，與您的應用程式的情況下儲存。  
  
         -或-  
  
    -   呼叫資料物件的`BeginEnumFormats`成員函式來開始列舉剪貼簿上可用的格式。 然後呼叫`GetNextFormat`直到返回剪貼簿格式應用程式所支援或有沒有更多的格式。  
  
 如果您使用`ON_UPDATE_COMMAND_UI`，您現在可以啟用貼上和，可能是 [編輯] 功能表上的選擇性貼上項目。 若要這樣做，請呼叫`CMenu::EnableMenuItem`或`CCmdUI::Enable`。 如需有關哪個容器應用程式應與功能表項目和，請參閱 <<c0> [ 功能表和資源： 容器新增](../mfc/menus-and-resources-container-additions.md)。  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a>從資料物件擷取資料  
 一旦您決定的資料格式，所有剩下的都只有從資料物件擷取資料。 若要這樣做，使用者會決定要放置資料和應用程式會呼叫適當的函式。 資料會是其中一個可用的下列媒體：  
  
|Medium|若要呼叫的函式|  
|------------|----------------------|  
|全域記憶體 (`HGLOBAL`)|`COleDataObject::GetGlobalData`|  
|檔案 (`CFile`)|`COleDataObject::GetFileData`|  
|**STGMEDIUM**結構 (`IStorage`)|`COleDataObject::GetData`|  
  
 常見的是，媒體將會連同其剪貼簿格式指定。 例如， **CF_EMBEDDEDSTRUCT**物件一律會處於`IStorage`中需要**STGMEDIUM**結構。 因此，您會使用`GetData`因為它是可以接受這些函式的唯一一個**STGMEDIUM**結構。  
  
 情況，剪貼簿格式中`IStream`或`HGLOBAL`架構可以提供中型`CFile`指標會參考資料。 應用程式接著可以使用它可能會從檔案匯入資料的相同方式取得資料讀取的檔案。 基本上，這是用戶端介面，以`OnRenderData`和`OnRenderFileData`資料來源中的常式。  
  
 使用者可以現在將資料插入文件就像任何其他資料格式相同。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [將拖放](../mfc/drag-and-drop-ole.md)  
  
-   [剪貼簿](../mfc/clipboard.md)  
  
## <a name="see-also"></a>請參閱  
 [資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject 類別](../mfc/reference/coledataobject-class.md)   
 [COleDataSource 類別](../mfc/reference/coledatasource-class.md)
