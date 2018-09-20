---
title: 虛擬清單控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5544582d65d84e95a22e78c9d663902d7df2dd24
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436035"
---
# <a name="virtual-list-controls"></a>虛擬清單控制項

虛擬清單控制項是具有 LVS_OWNERDATA 樣式的清單檢視控制項。 這個樣式可讓控制項來支援最多的項目計數**DWORD** (預設項目計數只會延伸到**int**)。 不過，此樣式所提供的最大優點是能夠在任何一次只能有在記憶體中的資料項目的子集。 這可讓虛擬清單檢視控制項本身大型資料庫的詳細資訊，用於存取資料的特定方法已採用。

> [!NOTE]
>  除了提供中的虛擬清單功能`CListCtrl`，MFC 也提供在相同的功能[CListView](../mfc/reference/clistview-class.md)類別。

有一些相容性問題，您應該注意的開發虛擬清單控制項時。 如需詳細資訊，請參閱 Windows SDK 中的清單檢視控制項主題中相容性問題的部分。

## <a name="handling-the-lvngetdispinfo-notification"></a>處理 LVN_GETDISPINFO 通知

虛擬清單控制項維護極少的項目資訊。 除了項目選取範圍和焦點的資訊，由控制項的擁有者管理所有項目資訊。 由架構透過 LVN_GETDISPINFO 通知訊息被要求之資訊。 若要提供所要求的資訊，虛擬清單控制項 （或控制項本身） 的擁有者必須處理此通知。 這可以輕鬆地完成使用 [屬性] 視窗 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。 產生的程式碼看起來應該類似下列的範例 (其中`CMyDialog`擁有虛擬清單控制項物件和對話方塊會處理通知):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

在 LVN_GETDISPINFO 通知訊息的處理常式，您必須檢查所要求的資訊類型。 可能值為：

- `LVIF_TEXT` *PszText*必須填入成員。

- `LVIF_IMAGE` *IImage*必須填入成員。

- `LVIF_INDENT` *IIndent*必須填入成員。

- `LVIF_PARAM` *LParam*必須填入成員。 （沒有子項目。）

- `LVIF_STATE` *狀態*必須填入成員。

然後，您應該提供給架構要求的資訊。

（取自清單控制項物件的通知處理常式的主體） 的下列範例會示範一個可行的方法，藉由提供的文字緩衝區和項目的映像的資訊：

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>快取和虛擬清單控制項

因為這種類型的清單控制項要用於大型資料集，建議您快取以改善擷取效能的要求的項目資料。 架構提供一個快取提示的機制，來協助您最佳化快取，方法是傳送 LVN_ODCACHEHINT 通知訊息。

下列範例會更新快取傳遞至處理常式函式的範圍。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

如需有關準備和維護快取的詳細資訊，請參閱 Windows SDK 中的清單檢視控制項主題的快取管理區段。

## <a name="finding-specific-items"></a>尋找特定的項目

虛擬清單控制項需要找到特定的清單控制項項目時，會傳送 LVN_ODFINDITEM 通知訊息。 當清單檢視控制項接收索引鍵的快速存取，或收到 LVM_FINDITEM 訊息時，會傳送通知訊息。 搜尋資訊的形式傳送**LVFINDINFO**結構，也就是成員的**NMLVFINDITEM**結構。 處理此訊息，藉由覆寫`OnChildNotify`清單中的函式控制物件，並在處理常式的主體內，檢查 LVN_ODFINDITEM 訊息。 如果找到，請執行適當的動作。

您應該準備好搜尋符合資訊清單檢視控制項所提供的項目。 如果不找到任何相符的項目，您應傳回索引的項目，如果成功，則為-1。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

