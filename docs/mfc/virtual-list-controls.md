---
title: 虛擬清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: a6e76a812a6196c487f72516e2b88198a544fdc7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907337"
---
# <a name="virtual-list-controls"></a>虛擬清單控制項

虛擬清單控制項是具有 LVS_OWNERDATA 樣式的清單視圖控制項。 此樣式可讓控制項支援最多**DWORD**的專案計數（預設專案計數只會延伸至**int**）。 不過，這種樣式所提供的最大優點，就是在任何時候都只能在記憶體中有資料項目子集的能力。 如此一來，虛擬清單視圖控制項就能與大型資料庫的資訊搭配使用，而這些資料的特定存取方法已準備就緒。

> [!NOTE]
>  除了在中`CListCtrl`提供虛擬清單功能，MFC 也會在[CListView](../mfc/reference/clistview-class.md)類別中提供相同的功能。

開發虛擬清單控制項時，有一些您應該注意的相容性問題。 如需詳細資訊，請參閱 Windows SDK 中的清單視圖控制項主題的相容性問題一節。

## <a name="handling-the-lvn_getdispinfo-notification"></a>處理 LVN_GETDISPINFO 通知

虛擬清單控制項會維護非常少的專案資訊。 除了專案選取範圍和焦點資訊之外，所有專案資訊都是由控制項的擁有者所管理。 架構會透過 LVN_GETDISPINFO 通知訊息來要求資訊。 若要提供要求的資訊，虛擬清單控制項（或控制項本身）的擁有者必須處理此通知。 這可以使用[類別 Wizard](reference/mfc-class-wizard.md)輕鬆完成（請參閱將[訊息對應至](../mfc/reference/mapping-messages-to-functions.md)函式）。 結果程式碼看起來應該如下列範例所示（ `CMyDialog`其中擁有虛擬清單控制項物件，而對話方塊正在處理通知）：

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

在 LVN_GETDISPINFO 通知訊息的處理常式中，您必須查看所要求的資訊類型。 可能值為：

- `LVIF_TEXT`*PszText*成員必須填入。

- `LVIF_IMAGE`*IImage*成員必須填入。

- `LVIF_INDENT`*IIndent*成員必須填入。

- `LVIF_PARAM`*LParam*成員必須填入。 （子專案不存在）。

- `LVIF_STATE`必須填入*狀態*成員。

接著，您應該提供向架構要求的任何資訊。

下列範例（取自清單控制項物件的通知處理常式主體）會藉由提供專案之文字緩衝區和影像的資訊，來示範一個可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>快取和虛擬清單控制項

由於這種類型的清單控制項適用于大型資料集，因此建議您快取要求的專案資料，以改善抓取效能。 此架構提供快取提示機制，藉由傳送 LVN_ODCACHEHINT 通知訊息來協助優化快取。

下列範例會使用傳遞至處理常式函式的範圍來更新快取。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

如需有關準備和維護快取的詳細資訊，請參閱 Windows SDK 中清單視圖控制項主題的 [快取管理] 區段。

## <a name="finding-specific-items"></a>尋找特定專案

當需要尋找特定的清單控制項專案時，虛擬清單控制項就會傳送 LVN_ODFINDITEM 通知訊息。 當清單視圖控制項收到快速存取金鑰或收到 LVM_FINDITEM 訊息時，就會傳送通知訊息。 搜尋資訊是以**LVFINDINFO**結構的形式傳送，這是**NMLVFINDITEM**結構的成員。 藉由覆寫`OnChildNotify`清單控制項物件的函式，並在處理常式主體內處理此訊息，檢查 LVN_ODFINDITEM 訊息。 如果找到，請執行適當的動作。

您應該準備好搜尋符合清單視圖控制項所提供之資訊的專案。 如果成功，您應該傳回專案的索引，如果找不到相符的專案，則傳回-1。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
