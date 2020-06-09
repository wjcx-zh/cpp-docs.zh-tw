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
ms.openlocfilehash: f1a83511edbf240d9a05d6d489f6cda9453ccea9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620407"
---
# <a name="data-objects-and-data-sources-manipulation"></a>資料物件和資料來源：管理

建立資料物件或資料來源之後，您可以對資料執行一些常見的作業，例如插入和移除資料、列舉資料所在的格式等等。 本文說明完成最常見作業所需的技巧。 主題包括：

- [將資料插入資料來源](#_core_inserting_data_into_a_data_source)

- [判斷資料物件中可用的格式](#_core_determining_the_formats_available_in_a_data_object)

- [從資料物件中抓取資料](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>將資料插入資料來源

將資料插入資料來源的方式，取決於資料是立即提供，還是視需要提供，以及在哪種媒體中提供。 可能的原因如下。

### <a name="supplying-data-immediately-immediate-rendering"></a>立即提供資料（立即轉譯）

- `COleDataSource::CacheGlobalData`針對您提供資料的每個剪貼簿格式重複呼叫。 傳遞要使用的剪貼簿格式，這是包含資料之記憶體的控制碼，也可以選擇描述資料的**FORMATETC**結構。

     -或-

- 如果您想要直接使用**STGMEDIUM**結構，您可以呼叫， `COleDataSource::CacheData` 而不是 `COleDataSource::CacheGlobalData` 上述選項中的。

### <a name="supplying-data-on-demand-delayed-rendering"></a>視需要提供資料（延遲轉譯）

這是一個先進的主題。

- `COleDataSource::DelayRenderData`針對您提供資料的每個剪貼簿格式重複呼叫。 傳遞要使用的剪貼簿格式，並選擇性地傳遞描述資料的**FORMATETC**結構。 當要求資料時，架構會呼叫 `COleDataSource::OnRenderData` ，而您必須覆寫此參數。

     -或-

- 如果您使用 `CFile` 物件來提供資料，請呼叫， `COleDataSource::DelayRenderFileData` 而不是 `COleDataSource::DelayRenderData` 在上一個選項中。 當要求資料時，架構會呼叫 `COleDataSource::OnRenderFileData` ，而您必須覆寫此參數。

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>判斷資料物件中可用的格式

在應用程式允許使用者將資料貼到其中之前，它必須知道剪貼簿上是否有可處理的格式。 若要這樣做，您的應用程式應該執行下列動作：

1. 建立 `COleDataObject` 物件和**FORMATETC**結構。

1. 呼叫資料物件的成員函式 `AttachClipboard` ，將資料物件與剪貼簿上的資料產生關聯。

1. 執行下列其中一個動作：

   - `IsDataAvailable`如果您只需要一或兩個格式，請呼叫資料物件的成員函式。 當剪貼簿上的資料支援的格式比您的應用程式大時，這會節省您的時間。

     \-或-

   - 呼叫資料物件的成員函式 `BeginEnumFormats` ，以開始列舉剪貼簿上可用的格式。 然後呼叫 `GetNextFormat` 直到剪貼簿傳回您的應用程式支援的格式，或沒有其他格式。

如果您使用**ON_UPDATE_COMMAND_UI**，您現在可以啟用 [編輯] 功能表上的 [貼上] 和 [可能貼上的特殊專案]。 若要這麼做，請呼叫 `CMenu::EnableMenuItem` 或 `CCmdUI::Enable` 。 如需容器應用程式應該如何使用功能表項目以及何時執行的詳細資訊，請參閱[功能表和資源：容器新增](menus-and-resources-container-additions.md)。

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>從資料物件中抓取資料

一旦決定了資料格式之後，剩下的就是從資料物件取得資料。 若要這麼做，使用者會決定要將資料放在何處，而應用程式會呼叫適當的函式。 資料將會在下列其中一種媒體中提供：

|中|要呼叫的函式|
|------------|----------------------|
|全域記憶體（ `HGLOBAL` ）|`COleDataObject::GetGlobalData`|
|File （ `CFile` ）|`COleDataObject::GetFileData`|
|**STGMEDIUM**結構（ `IStorage` ）|`COleDataObject::GetData`|

通常，媒體會連同其剪貼簿格式一起指定。 例如， **CF_EMBEDDEDSTRUCT**物件一定會在 `IStorage` 需要**STGMEDIUM**結構的媒體中。 因此，您會使用， `GetData` 因為它是其中一個可接受**STGMEDIUM**結構的函式。

若為剪貼簿格式位於或媒體中的情況 `IStream` `HGLOBAL` ，架構可以提供 `CFile` 參考資料的指標。 然後，應用程式可以使用「檔案讀取」來取得資料，就像從檔案匯入資料的方式一樣。 基本上，這是 `OnRenderData` 資料來源中和常式的用戶端介面 `OnRenderFileData` 。

使用者現在可以將資料插入檔中，就像任何其他具有相同格式的資料一樣。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [拖放功能](drag-and-drop-ole.md)

- [剪貼簿](clipboard.md)

## <a name="see-also"></a>另請參閱

[資料物件和資料來源 (OLE)](data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 類別](reference/coledataobject-class.md)<br/>
[COleDataSource 類別](reference/coledatasource-class.md)
