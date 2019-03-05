---
title: 資料物件和資料來源：操作
ms.date: 11/04/2016
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
ms.openlocfilehash: 81dfe911866c4d1ba1720ee2c9854076c499f0a3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286747"
---
# <a name="data-objects-and-data-sources-manipulation"></a>資料物件和資料來源：操作

建立資料物件或資料來源之後，您可以執行上的資料，例如插入和移除資料，列舉資料所在的格式，以及其他常見作業的數量。 這篇文章描述完成最常見的作業所需的方法。 主題包括：

- [將資料插入至資料來源](#_core_inserting_data_into_a_data_source)

- [判斷資料物件中可用的格式](#_core_determining_the_formats_available_in_a_data_object)

- [從資料物件擷取資料](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a> 將資料插入至資料來源

資料插入到資料來源的方式取決於資料是否立即提供或依需求，以及以何種媒體會提供。 可能值如下所示。

### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供資料 （立即轉譯）

- 呼叫`COleDataSource::CacheGlobalData`重複為您提供資料的每個剪貼簿格式。 將剪貼簿格式，才能使用，包含資料的記憶體的控制代碼，並選擇性地**FORMATETC**結構描述的資料。

     -或-

- 如果您想要直接使用**STGMEDIUM**結構，呼叫`COleDataSource::CacheData`而不是`COleDataSource::CacheGlobalData`在上述的選項。

### <a name="supplying-data-on-demand-delayed-rendering"></a>提供隨選 （延遲轉譯） 的資料

這是進階的主題。

- 呼叫`COleDataSource::DelayRenderData`重複為您提供資料的每個剪貼簿格式。 傳遞所要使用剪貼簿格式，並選擇性地**FORMATETC**結構描述的資料。 當要求資料時，架構會在呼叫`COleDataSource::OnRenderData`，您必須覆寫。

     -或-

- 如果您使用`CFile`物件來提供資料，呼叫`COleDataSource::DelayRenderFileData`而不是`COleDataSource::DelayRenderData`中前一個選項。 當要求資料時，架構會在呼叫`COleDataSource::OnRenderFileData`，您必須覆寫。

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> 判斷資料物件中可用的格式

應用程式可讓使用者貼上資料之前，它需要知道它可以處理的剪貼簿上是否有格式。 若要這樣做，您的應用程式應該執行下列作業：

1. 建立`COleDataObject`物件和**FORMATETC**結構。

1. 呼叫資料物件的`AttachClipboard`剪貼簿上的資料相關聯的資料物件的成員函式。

1. 執行下列任一步驟：

   - 呼叫資料物件的`IsDataAvailable`成員函式，如果有只有一個或兩個格式化您的需要。 這會節省您時間在剪貼簿上的資料，支援更多的格式，與您的應用程式的情況下。

         -or-

   - 呼叫資料物件的`BeginEnumFormats`成員函式來開始列舉剪貼簿上可用的格式。 然後呼叫`GetNextFormat`直到剪貼簿傳回應用程式所支援的格式，或有沒有更多的格式。

如果您使用**ON_UPDATE_COMMAND_UI**，您現在可以啟用貼上和，可能的話，[編輯] 功能表上的選擇性貼上項目。 若要這樣做，請呼叫`CMenu::EnableMenuItem`或`CCmdUI::Enable`。 如需有關哪些容器應用程式應該使用功能表項目進行，請參閱 <<c0> [ 功能表和資源：容器新增](../mfc/menus-and-resources-container-additions.md)。

##  <a name="_core_retrieving_data_from_a_data_object"></a> 從資料物件擷取資料

一旦您決定的資料格式，都是從資料物件擷取資料。 若要這樣做，使用者會決定要放置資料和應用程式會呼叫適當的函式。 資料將可在其中一個下列的媒體：

|Medium|若要呼叫的函式|
|------------|----------------------|
|全域記憶體 (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|檔案 (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM**結構 (`IStorage`)|`COleDataObject::GetData`|

通常，媒體將會指定連同其剪貼簿格式。 例如， **CF_EMBEDDEDSTRUCT**物件一律會處於`IStorage`需要的中型**STGMEDIUM**結構。 因此，您會使用`GetData`因為它是唯一可以接受這些函式**STGMEDIUM**結構。

案例的剪貼簿格式會處於`IStream`或`HGLOBAL`架構可以提供中型`CFile`參考資料的指標。 應用程式接著可以使用讀取的檔案來取得中大部分的資料相同的方式，因為它可能會從檔案匯入資料。 基本上，這是用戶端介面，以`OnRenderData`和`OnRenderFileData`資料來源中的常式。

使用者可以現在將資料插入文件就像任何其他資料格式相同。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [將拖放](../mfc/drag-and-drop-ole.md)

- [剪貼簿](../mfc/clipboard.md)

## <a name="see-also"></a>另請參閱

[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 類別](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)
