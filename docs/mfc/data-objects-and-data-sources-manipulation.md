---
title: 資料物件和資料來源：管理
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
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370556"
---
# <a name="data-objects-and-data-sources-manipulation"></a>資料物件和資料來源：管理

建立資料物件或資料源後,可以對資料執行許多常見操作,例如插入和刪除數據、枚舉數據中的格式等。 本文介紹了完成最常見操作所需的技術。 主題包括：

- [將資料插入資料來源](#_core_inserting_data_into_a_data_source)

- [確定資料物件中可用的格式](#_core_determining_the_formats_available_in_a_data_object)

- [從資料物件檢索資料](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>將資料插入資料來源

數據如何插入到數據源取決於數據是立即提供還是按需提供,以及數據在哪個介質中提供。 可能性如下。

### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供資料(立即呈現)

- 重複`COleDataSource::CacheGlobalData`調用提供資料的每個剪貼簿格式。 傳遞要使用的剪貼簿格式、包含資料的記憶體的句柄,以及描述數據的**FORMATETC**結構。

     -或-

- 如果要直接使用**STGMEDIUM**結構,請`COleDataSource::CacheData`呼`COleDataSource::CacheGlobalData`叫而不是在上面的選項中。

### <a name="supplying-data-on-demand-delayed-rendering"></a>依需提供資料(延遲渲染)

這是一個高級主題。

- 重複`COleDataSource::DelayRenderData`調用提供資料的每個剪貼簿格式。 傳遞要使用的剪貼簿格式,以及(可選)描述數據的**FORMATETC**結構。 要求資料時,框架將呼叫`COleDataSource::OnRenderData`必須覆寫的 。

     -或-

- 如果使用`CFile`物件提供數據,請呼`COleDataSource::DelayRenderFileData`叫`COleDataSource::DelayRenderData`而不是在前面的選項中。 要求資料時,框架將呼叫`COleDataSource::OnRenderFileData`必須覆寫的 。

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>確定資料物件中可用的格式

在應用程式允許使用者將數據貼貼到其中之前,它需要知道剪貼簿上是否有可以處理的格式。 為此,應用程式應執行以下操作:

1. 創建`COleDataObject`物件和**FORMATETC**結構。

1. 調用數據物件`AttachClipboard`的成員函數,將數據物件與剪貼簿上的數據相關聯。

1. 執行下列其中一個動作：

   - 如果只需要一種或兩`IsDataAvailable`種格式,請調用數據對象的成員函數。 如果剪貼簿上的數據支援格式明顯多於應用程式,這將節省您的時間。

     \-或-

   - 呼叫資料物件`BeginEnumFormats`的成員函數開始枚舉剪貼簿上可用的格式。 然後呼叫`GetNextFormat`,直到剪貼簿返回應用程式支援的格式或沒有更多格式。

如果使用**ON_UPDATE_COMMAND_UI**,現在可以啟用"粘貼",並可能在"編輯"功能表上粘貼特殊專案。 為此,請呼叫`CMenu::EnableMenuItem`任`CCmdUI::Enable`一或 。 有關容器應用程式應如何處理選單項目以及何時執行的詳細資訊,請參閱[選單和資源:容器添加](../mfc/menus-and-resources-container-additions.md)。

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>從資料物件檢索資料

決定數據格式后,剩下的就是從數據對象中檢索數據。 為此,用戶決定將數據放在何處,應用程式調用相應的函數。 資料將在以下媒體之一提供:

|中|呼叫函數|
|------------|----------------------|
|全域記憶體`HGLOBAL`( )|`COleDataObject::GetGlobalData`|
|檔案`CFile`( )|`COleDataObject::GetFileData`|
|**STGMEDIUM**`IStorage`結構( )|`COleDataObject::GetData`|

通常,媒體將與其剪貼簿格式一起指定。 例如 **,CF_EMBEDDEDSTRUCT**對象`IStorage`始終位於需要**STGMEDIUM**結構的介質中。 因此,您將使用`GetData`,因為它是這些函數中唯一可以接受**STGMEDIUM**結構的功能。

對於剪貼簿格式處於`IStream``HGLOBAL`或媒體中的情況,架構可以提供引用資料的`CFile`指標。 然後,應用程式可以使用檔讀取來獲取數據的方式與從檔導入數據的方式大致相同。 本質上,這是數據源中`OnRenderData``OnRenderFileData`和例程的用戶端介面。

用戶現在可以像將相同格式的任何其他數據一樣將數據插入到文檔中。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [拖放](../mfc/drag-and-drop-ole.md)

- [剪貼簿](../mfc/clipboard.md)

## <a name="see-also"></a>另請參閱

[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 類別](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)
