---
title: OLE 拖放
description: 概述 Microsoft Foundation class （MFC） OLE 拖放、如何執行卸載來源、放置目標，以及如何自訂拖放。
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: c601e8f0324510346513dc8da48dd1a83c95bceb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420348"
---
# <a name="ole-drag-and-drop"></a>OLE 拖放

OLE 的拖放功能主要是複製並貼上資料的捷徑。 當您使用 [剪貼簿] 複製或貼上資料時，需要幾個步驟。 您可以選取資料，然後從 [**編輯**] 功能表選擇 [**剪**下] 或 [**複製**]。 然後，移至目的地應用程式或視窗，並將游標放在目標位置。 最後，您可以從功能表中選擇 [**編輯** > **貼**上]。

OLE 拖放功能與檔案管理員拖放機制不同。 [檔案管理員] 只能處理檔案名，而且是專門為了將檔案名傳遞給應用程式而設計的。 OLE 中的拖放功能更為普遍。 它允許您拖放可以放置在剪貼簿上的任何資料。

當您使用 OLE 拖放時，您會從整個流程中移除兩個步驟。 您可以從來源視窗（「卸載來源」）選取資料，然後將它拖曳到目的地（「卸載目標」）。 您可以放開滑鼠按鍵來放置它。 此作業不需要功能表，而且速度會比複製/貼上序列更快。 只有一個需求： [卸載來源] 和 [卸載目標] 都必須開啟，而且在畫面上至少有部分可見。

您可以使用 OLE 拖放，輕鬆地將資料從一個位置傳輸到另一個位置：在檔中、在不同的檔之間，或是在應用程式之間。 它可能會在容器或伺服器應用程式中執行。 任何應用程式都可以是拖放來源、放置目標或兩者。 如果應用程式同時執行了放置來源和放置目標的支援，您可以在子視窗之間或在一個視窗內拖放。 這項功能可讓您的應用程式更容易使用。

[資料物件和資料來源（OLE）](../mfc/data-objects-and-data-sources-ole.md)文章說明如何在您的應用程式中執行資料傳輸。 檢查 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)也很有説明。

## <a name="implement-a-drop-source"></a>執行 drop source

若要讓您的應用程式提供資料給拖放作業，請執行 drop source。 Drop source 的基本執行相當簡單。 第一個步驟是判斷哪些事件開始拖曳作業。 建議的使用者介面指導方針會定義拖曳作業的開始，如同在某些選取的資料內的某個時間點發生**WM_LBUTTONDOWN**事件時。 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)和[HIERSVR](../overview/visual-cpp-samples.md)遵循這些指導方針。

如果您的應用程式是容器，而選取的資料是 `COleClientItem`類型的連結或内嵌物件，請呼叫其 `DoDragDrop` 成員函式。 否則，請使用選取專案來建立 `COleDataSource` 物件、將它初始化，然後呼叫資料來源物件的 `DoDragDrop` 成員函式。 如果您的應用程式是伺服器，請使用 `COleServerItem::DoDragDrop`。 如需自訂標準拖放行為的詳細資訊，請參閱[自訂拖放](#customize-drag-and-drop)一節。

如果 `DoDragDrop` 傳回**DROPEFFECT_MOVE**，請立即刪除來源文件中的來源資料。 `DoDragDrop` 中沒有任何其他傳回值會對 drop source 造成任何影響。

如需詳細資訊，請參閱[OLE 資料物件和資料來源：建立和銷毀](../mfc/data-objects-and-data-sources-creation-and-destruction.md)和[OLE 資料物件和資料來源：操作](../mfc/data-objects-and-data-sources-manipulation.md)\.

## <a name="implement-a-drop-target"></a>執行放置目標

相較于卸載來源，執行放置目標的工作會稍微多一點，但是它仍然相當簡單。

### <a name="to-implement-an-ole-drop-target"></a>若要執行 OLE 放置目標

1. 如果尚未存在，請在應用程式的 `InitInstance` 成員函式中，新增對 `AfxOleInit` 的呼叫。 這是初始化 OLE 程式庫所需的呼叫。

1. 將成員變數加入至應用程式中您想要成為放置目標的每個視圖。 這個成員變數的類型必須是 `COleDropTarget` 或衍生自它的類別。

1. 從處理**WM_CREATE**訊息的 view 類別函式（通常是 `OnCreate`），呼叫新成員變數的 `Register` 成員函式。 當您的視圖終結時，系統會自動為您呼叫 `Revoke`。

1. 覆寫下列函數。 如果您想要在整個應用程式中都有相同的行為，請覆寫 view 類別中的這些函式。 如果您想要修改隔離案例中的行為，或想要在非`CView` 的視窗上進行卸載，請在您的 `COleDropTarget`衍生類別中覆寫這些函式。

   | 覆寫 | 允許 |
   | -------- | -------- |
   | `OnDragEnter` | 放置要在視窗中發生的作業。 在資料指標第一次進入視窗時呼叫。 |
   | `OnDragLeave` | 當拖曳作業離開指定的視窗時的特殊行為。 |
   | `OnDragOver` | 放置要在視窗中發生的作業。 將游標拖曳至視窗時呼叫。 |
   | `OnDrop` | 處理要放入指定視窗中的資料。 |
   | `OnScrollBy` | 在目標視窗中需要滾動時的特殊行為。 |

請參閱 MAINVIEW。屬於 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)的 CPP 檔案，是這些函式如何一起運作的範例。

如需詳細資訊，請參閱[OLE 資料物件和資料來源：建立和銷毀](../mfc/data-objects-and-data-sources-creation-and-destruction.md)和[OLE 資料物件和資料來源：操作](../mfc/data-objects-and-data-sources-manipulation.md)\.

## <a name="customize-drag-and-drop"></a>自訂拖放

拖放功能的預設實作對大部分應用程式而言已經足夠。 不過，有些應用程式可能會要求您變更此標準行為。 本節說明變更這些預設值所需的步驟。 您可以使用這項技術，讓不支援複合檔案的應用程式進入捨棄來源。

如果您要自訂標準 OLE 拖放行為，或您有非 OLE 應用程式，您必須建立 `COleDataSource` 物件來包含資料。 當使用者開始拖放作業時，您的程式碼應該從此物件而不是從其他支援拖放作業的類別呼叫 `DoDragDrop` 函式。

或者，您可以建立 `COleDropSource` 物件來控制置放並且根據您要變更的行為類型覆寫其中的一些函式。 這個置放來源物件隨後會傳遞至 `COleDataSource::DoDragDrop`，以變更這些函式的預設行為。 這些不同選項可讓您在支援應用程式的拖放作業時擁有更多的彈性。 如需資料來源的詳細資訊，請參閱[資料物件和資料來源（OLE）](../mfc/data-objects-and-data-sources-ole.md)一文。

您可以覆寫下列函式以自訂拖放作業：

| 覆寫 | 自訂 |
| -------- | ------------ |
| `OnBeginDrag` | 在您呼叫 `DoDragDrop`之後，如何開始拖曳作業。 |
| `GiveFeedback` | 不同置放結果的視覺化回饋，例如游標外觀。 |
| `QueryContinueDrag` | 拖放作業的終止。 此函式可讓您在拖曳作業期間檢查輔助按鍵狀態。 |

## <a name="see-also"></a>另請參閱

[OLE](../mfc/ole-in-mfc.md)\
[OLE 資料物件和資料來源](../mfc/data-objects-and-data-sources-ole.md)\
[OLE 資料物件和資料來源：建立和銷毀](../mfc/data-objects-and-data-sources-creation-and-destruction.md)\
[OLE 資料物件和資料來源：操作](../mfc/data-objects-and-data-sources-manipulation.md)\
[COleClientItem：:D odragdrop](../mfc/reference/coleclientitem-class.md#dodragdrop)\
[COleDataSource 類別](../mfc/reference/coledatasource-class.md)\
[COleDataSource：:D odragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)\
[COleDropSource 類別](../mfc/reference/coledropsource-class.md)\
[COleDropTarget 類別](../mfc/reference/coledroptarget-class.md)\
[CView：： System.windows.uielement.ondragleave](../mfc/reference/cview-class.md#ondragleave)
