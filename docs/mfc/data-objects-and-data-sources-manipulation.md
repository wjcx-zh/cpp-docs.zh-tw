---
title: "資料物件和資料來源：管理 | Microsoft Docs"
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
  - "剪貼簿 [C++], 判斷可用格式"
  - "剪貼簿 [C++], 傳遞格式資訊"
  - "資料物件 [C++], 操作"
  - "資料來源 [C++], 資料作業"
  - "資料來源 [C++], 判斷可用格式"
  - "資料來源 [C++], 插入資料"
  - "延遲呈現 [C++]"
  - "OLE [C++], 資料物件"
  - "OLE [C++], 資料來源"
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料物件和資料來源：管理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在資料物件或資料來源建立之後，您可以對資料的一些一般作業，例如插入，並移除資料，列舉格式資料等等。  本文說明必要的技術完成最常見的作業。  主題包括：  
  
-   [將資料插入至資料來源](#_core_inserting_data_into_a_data_source)  
  
-   [判斷格式可用資料物件](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [從資料物件擷取資料物件。](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a> 將資料插入至資料來源  
 資料的方式插入資料來源取決於是否立即提供資料或控制項，因此，在哪媒體它提供。  可能值如下。  
  
### 提供的資料立即 \(立即計算色彩\)  
  
-   呼叫以 `COleDataSource::CacheGlobalData` 為您提供資料的每個剪貼簿格式。  透過剪貼簿格式會用的控制代碼，記憶體中的資料，而且，或者，描述資料的 **FORMATETC** 結構。  
  
     \-或\-  
  
-   如果您想要直接使用 **STGMEDIUM** 結構時，呼叫 `COleDataSource::CacheData` 而不是在上面選項的 `COleDataSource::CacheGlobalData` 。  
  
### 提供的資料控制項 \(延遲轉譯\)  
 這是一個進階主題。  
  
-   呼叫以 `COleDataSource::DelayRenderData` 為您提供資料的每個剪貼簿格式。  透過剪貼簿格式將使用，而且，或者，描述資料的 **FORMATETC** 結構。  當資料要求，架構會呼叫 `COleDataSource::OnRenderData`，就必須覆寫。  
  
     \-或\-  
  
-   如果您使用 `CFile` 物件提供資料，請呼叫 `COleDataSource::DelayRenderFileData` 而不是在上一個索引標籤的 `COleDataSource::DelayRenderData` 。  當資料要求，架構會呼叫 `COleDataSource::OnRenderFileData`，就必須覆寫。  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> 判斷格式可用資料物件  
 在應用程式允許使用者貼上資料至之前，它必須知道是否有在它可以處理的剪貼簿格式。  若要這樣做，您的應用程式應該執行下列作業:  
  
1.  建立 `COleDataObject` 物件和 **FORMATETC** 結構。  
  
2.  呼叫資料物件的 `AttachClipboard` 成員函式相關聯的資料物件與剪貼簿上的資料。  
  
3.  執行下列任一步驟：  
  
    -   呼叫資料物件的 `IsDataAvailable` 成員函式是否只需要的兩種格式。  在剪貼簿上的資料與您的應用程式所支援的格式，這樣可以節省時間。  
  
         \-或\-  
  
    -   呼叫資料物件的 `BeginEnumFormats` 成員函式開始列舉格式可用在剪貼簿上。  然後呼叫 `GetNextFormat` ，直到剪貼簿格式傳回應用程式支援或沒有其他格式。  
  
 如果您使用 `ON_UPDATE_COMMAND_UI`，您現在可以使貼上，而，可能，貼在編輯功能表的特殊項目。  若要這麼做，請呼叫 `CMenu::EnableMenuItem` 或 `CCmdUI::Enable`。  如需功能的詳細資訊容器應用程式應該對功能表項目，然後，如果為，請參閱 [功能表和資源:加入容器](../mfc/menus-and-resources-container-additions.md)。  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a> 從資料物件擷取資料  
 一旦決定了資料格式，所有保持為從資料物件擷取資料。  若要這樣做，使用者在何處決定放置資料，因此，應用程式會呼叫適當的函式。  資料在下列媒體其中之一可以:  
  
|中|呼叫的函式|  
|-------|-----------|  
|全域記憶體 \(`HGLOBAL`\)|`COleDataObject::GetGlobalData`|  
|檔案 \(`CFile`\)|`COleDataObject::GetFileData`|  
|**STGMEDIUM** 結構 \(`IStorage`\)|`COleDataObject::GetData`|  
  
 通常，媒體會使用自己的剪貼簿格式一起指定。  例如， **CF\_EMBEDDEDSTRUCT** 物件永遠在需要 **STGMEDIUM** 的 `IStorage` 和媒體。  因此，您會使用 `GetData` ，因為它是可以接受 **STGMEDIUM** 結構的它在這些函式。  
  
 如果剪貼簿格式在 `IStream` 或 `HGLOBAL` 媒體的情況下，架構可以提供參考資料的 `CFile` 指標。  應用程式可以使用讀取的檔案取得資料，以與它可能匯入資料從檔案相同。  基本上，這是用戶端介面至資料來源的 `OnRenderData` 和 `OnRenderFileData` 常式。  
  
 使用者現在可以將資料插入至文件像在相同格式的其他資料。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [拖放](../mfc/drag-and-drop-ole.md)  
  
-   [剪貼簿](../mfc/clipboard.md)  
  
## 請參閱  
 [資料物件和資料來源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)