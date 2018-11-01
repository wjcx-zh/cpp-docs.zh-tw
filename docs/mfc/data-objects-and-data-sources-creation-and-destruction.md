---
title: 資料物件和資料來源：建立和解構
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: a46cc15a101618699b9e7fa988155517de673fdb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614964"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>資料物件和資料來源：建立和解構

在本文中所述[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)，資料物件和資料來源代表資料傳輸的兩邊。 本文說明建立和終結這些物件和來源的時機，以適當地執行資料傳輸，包括：

- [建立資料物件](#_core_creating_data_objects)

- [終結資料物件](#_core_destroying_data_objects)

- [建立資料來源](#_core_creating_data_sources)

- [終結資料來源](#_core_destroying_data_sources)

##  <a name="_core_creating_data_objects"></a> 建立資料物件

資料物件是由目的端應用程式 (可以是用戶端或伺服器) 所使用。 目的端應用程式中的資料物件是來源應用程式和目的端應用程式間連線的一端。 目的端應用程式中的資料物件用於存取及與資料來源中的資料進行互動。

有兩種常見的情況需要資料物件。 第一種情況是使用拖放方式將資料放入應用程式。 第二種情況是從 [編輯] 功能表中選擇 [貼上] 或 [選擇性貼上]。

在使用拖放的情況下，您不需要建立資料物件。 現有資料物件的指標會傳遞至您的 `OnDrop` 函式。 這個資料物件是由架構建立做為拖放作業的一部分，而且也會由它來終結。 如果是使用其他方貼上內容時，就不一定會以此方式完成。 如需詳細資訊，請參閱 <<c0> [ 終結資料物件](#_core_destroying_data_objects)。

如果應用程式會執行貼上或選擇性貼上動作，您應該建立 `COleDataObject` 物件並呼叫它的 `AttachClipboard` 成員函式。 這麼做會讓資料物件與剪貼簿上的資料產生關聯。 接著您可以在貼上函式中使用這個資料物件。

##  <a name="_core_destroying_data_objects"></a> 終結資料物件

如果您依照所述的配置[建立資料物件](#_core_creating_data_objects)，終結資料物件是資料傳輸的一般層面。 當您的貼上函式傳回時，在您的貼上函式中建立的資料物件會由 MFC 進行終結。

如果您使用其他處理貼上作業的方法，請在貼上作業完成之後確定資料物件已終結。 資料物件終結後，任何應用程式將無法複製資料到剪貼簿。

##  <a name="_core_creating_data_sources"></a> 建立資料來源

資料來源是由資料傳輸的來源使用，可以是資料傳輸的用戶端或伺服器端。 來源端應用程式中的資料來源是來源應用程式和目的端應用程式間連線的一端。 目的端應用程式中的資料物件是用來與資料來源中的資料互動。

當應用程式需要將資料複製到剪貼簿時，會建立資料來源。 一般的執行案例會像這樣：

1. 使用者選取一些資料。

1. 使用者選擇**複製**(或**剪下**) 從**編輯**功能表或開始拖放作業。

1. 根據程式的設計，應用程式會建立一個 `COleDataSource` 物件或衍生自 `COleDataSource` 類別的物件。

1. 選取的資料會藉由在 `COleDataSource::CacheData` 或 `COleDataSource::DelayRenderData` 群組中呼叫其中一個函式，以插入資料來源。

1. 應用程式會呼叫 `SetClipboard` 成員函式 (如果為拖放作業，則呼叫 `DoDragDrop` 成員函式)，該成員函式是屬於在第 3 個步驟中建立的物件。

1. 如果是這**剪下**作業或`DoDragDrop`會傳回**DROPEFFECT_MOVE**，從文件中刪除選取在步驟 1 中的資料。

此案例中藉由 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)並[HIERSVR](../visual-cpp-samples.md)。 針對每個應用程式的 `CView` 衍生類別查看除了 `GetClipboardData` 和 `OnGetClipboardData` 函式之外的原始程式碼。 這兩個函式會位於 `COleClientItem` 或 `COleServerItem` 衍生類別的實作中。 這些範例程式為如何實作這些概念提供了良好的範例。

如果要修改拖放作業的預設行為，會發生另一種您可能想要建立 `COleDataSource` 物件的情況。 如需詳細資訊，請參閱 <<c0> [ 拖放： 自訂](../mfc/drag-and-drop-customizing.md)文章。

##  <a name="_core_destroying_data_sources"></a> 終結資料來源

目前負責它們的應用程式必須終結資料來源。 在其中您將資料來源交給 OLE 的情況下，例如呼叫[coledatasource:: Dodragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)，您必須呼叫`pDataSrc->InternalRelease`。 例如: 

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

如果您未將資料來源交給 OLE，則您必須負責終結該資料來源，方法和一般的 C++ 物件相同。

如需詳細資訊，請參閱 <<c0> [ 拖放](../mfc/drag-and-drop-ole.md)，[剪貼簿](../mfc/clipboard.md)，並[操作資料物件和資料來源](../mfc/data-objects-and-data-sources-manipulation.md)。

## <a name="see-also"></a>另請參閱

[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 類別](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)
