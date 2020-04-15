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
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371208"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>資料物件和資料來源：建立和解構

如文章《[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)中所述,數據物件和數據源表示數據傳輸的兩面。 本文說明建立和終結這些物件和來源的時機，以適當地執行資料傳輸，包括：

- [建立資料物件](#_core_creating_data_objects)

- [銷毀資料物件](#_core_destroying_data_objects)

- [建立資料來源](#_core_creating_data_sources)

- [銷毀資料來源](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>建立資料物件

資料物件是由目的端應用程式 (可以是用戶端或伺服器) 所使用。 目的端應用程式中的資料物件是來源應用程式和目的端應用程式間連線的一端。 目的端應用程式中的資料物件用於存取及與資料來源中的資料進行互動。

有兩種常見的情況需要資料物件。 第一種情況是使用拖放方式將資料放入應用程式。 第二種情況是從 [編輯] 功能表中選擇 [貼上] 或 [選擇性貼上]。

在使用拖放的情況下，您不需要建立資料物件。 現有資料物件的指標會傳遞至您的 `OnDrop` 函式。 這個資料物件是由架構建立做為拖放作業的一部分，而且也會由它來終結。 如果是使用其他方貼上內容時，就不一定會以此方式完成。 有關詳細資訊,請參閱[銷資料物件](#_core_destroying_data_objects)。

如果應用程式會執行貼上或選擇性貼上動作，您應該建立 `COleDataObject` 物件並呼叫它的 `AttachClipboard` 成員函式。 這麼做會讓資料物件與剪貼簿上的資料產生關聯。 接著您可以在貼上函式中使用這個資料物件。

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>銷毀資料物件

如果您遵循[「創建資料物件」](#_core_creating_data_objects)中描述的方案,則銷毀數據對像是資料傳輸的一個微不足道的方面。 當您的貼上函式傳回時，在您的貼上函式中建立的資料物件會由 MFC 進行終結。

如果您使用其他處理貼上作業的方法，請在貼上作業完成之後確定資料物件已終結。 資料物件終結後，任何應用程式將無法複製資料到剪貼簿。

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>建立資料來源

資料來源是由資料傳輸的來源使用，可以是資料傳輸的用戶端或伺服器端。 來源端應用程式中的資料來源是來源應用程式和目的端應用程式間連線的一端。 目的端應用程式中的資料物件是用來與資料來源中的資料互動。

當應用程式需要將資料複製到剪貼簿時，會建立資料來源。 一般的執行案例會像這樣：

1. 使用者選取一些資料。

1. 使用者從 **「編輯」** 選單中選擇 **「複製**」(或**剪切**)」或開始拖放操作。

1. 根據程式的設計，應用程式會建立一個 `COleDataSource` 物件或衍生自 `COleDataSource` 類別的物件。

1. 選取的資料會藉由在 `COleDataSource::CacheData` 或 `COleDataSource::DelayRenderData` 群組中呼叫其中一個函式，以插入資料來源。

1. 應用程式會呼叫 `SetClipboard` 成員函式 (如果為拖放作業，則呼叫 `DoDragDrop` 成員函式)，該成員函式是屬於在第 3 個步驟中建立的物件。

1. 如果這是 **「剪切」**`DoDragDrop`操作或返回**DROPEFFECT_MOVE,** 則步驟 1 中選擇的數據將從文檔中刪除。

此方案由 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)實現。 針對每個應用程式的 `CView` 衍生類別查看除了 `GetClipboardData` 和 `OnGetClipboardData` 函式之外的原始程式碼。 這兩個函式會位於 `COleClientItem` 或 `COleServerItem` 衍生類別的實作中。 這些範例程式為如何實作這些概念提供了良好的範例。

如果要修改拖放作業的預設行為，會發生另一種您可能想要建立 `COleDataSource` 物件的情況。 有關詳細資訊,請參閱 OLE[拖放:自定義拖放](../mfc/drag-and-drop-ole.md#customize-drag-and-drop)文章。

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>銷毀資料來源

目前負責它們的應用程式必須終結資料來源。 在將資料來源交給 OLE 的情況下,例如呼叫[COleDataSource::DoDragDrop),](../mfc/reference/coledatasource-class.md#dodragdrop)`pDataSrc->InternalRelease`您需要呼叫 。 例如：

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

如果您未將資料來源交給 OLE，則您必須負責終結該資料來源，方法和一般的 C++ 物件相同。

關於詳細資訊,請參閱[拖曳](../mfc/drag-and-drop-ole.md)、[剪貼簿](../mfc/clipboard.md)與[操作資料物件與資料來源](../mfc/data-objects-and-data-sources-manipulation.md)。

## <a name="see-also"></a>另請參閱

[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 類別](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)
