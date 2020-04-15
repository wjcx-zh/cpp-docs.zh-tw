---
title: 虛擬清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375522"
---
# <a name="virtual-list-controls"></a>虛擬清單控制項

虛擬清單控制項是具有LVS_OWNERDATA樣式的清單檢視控制項。 此樣式使控制項能夠支援最多到**DWORD**的項計數(預設項計數僅擴展到**int**)。 但是,此樣式提供的最大優勢是能夠在任何時候僅具有記憶體中的數據項子集。 這允許虛擬清單檢視控制項適合用於大型資訊資料庫,其中已具有訪問數據的特定方法。

> [!NOTE]
> 除了在`CListCtrl`中 提供虛擬清單功能外,MFC 還在[CListView](../mfc/reference/clistview-class.md)類中提供了相同的功能。

在開發虛擬清單控制項時,您應該注意一些相容性問題。 有關詳細資訊,請參閱 Windows SDK 中的「清單-查看控制件」主題的相容性問題部分。

## <a name="handling-the-lvn_getdispinfo-notification"></a>處理LVN_GETDISPINFO通知

虛擬清單控制項維護的專案資訊很少。 除物料選擇和焦點資訊外,所有物料資訊都由控件的所有者管理。 框架通過LVN_GETDISPINFO通知消息請求資訊。 要提供請求的信息,虛擬清單控制件的擁有者(或控件本身)必須處理此通知。 這可以很容易地使用[類嚮導](reference/mfc-class-wizard.md)完成(請參閱[將消息映射到函數](../mfc/reference/mapping-messages-to-functions.md))。 由此產生的代碼應類似於以下範例(其中`CMyDialog`擁有虛擬清單控制項物件,對話框正在處理通知):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

在LVN_GETDISPINFO通知消息的處理程式中,必須檢查請求的資訊類型。 可能的值包括：

- `LVIF_TEXT`必須填寫*pszText*成員。

- `LVIF_IMAGE`必須填寫*iImage*成員。

- `LVIF_INDENT`必須填寫*iIndent*成員。

- `LVIF_PARAM`必須填寫*lParam*成員。 (子項不存在。

- `LVIF_STATE`必須填寫*國務委員*。

然後,您應該提供請求回框架的任何資訊。

以下範例(從清單控制項物件的通知處理程式正文中)演示了一種可能的方法,方法是為專案的文本緩衝區和影像提供資訊:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>快取及虛擬清單控制項

由於這種類型的清單控制項適用於大型資料集,因此建議您快取請求的項資料以提高檢索性能。 該框架提供了一種緩存提示機制,通過發送LVN_ODCACHEHINT通知消息來幫助優化緩存。

下面的範例使用傳遞給處理程式函數的範圍更新緩存。

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

有關準備和維護快取的詳細資訊,請參閱 Windows SDK 中的「清單查看控制件」主題的快取管理部分。

## <a name="finding-specific-items"></a>尋找特定項目

當需要找到特定清單控制項時,虛擬清單控制項將發送LVN_ODFINDITEM通知訊息。 當清單檢視控制件收到快速金鑰訪問或收到LVM_FINDITEM消息時,將發送通知消息。 搜尋資訊以**LVFINDINFO**結構的形式發送,該結構是**NMLVFINDITEM**結構的成員。 通過重寫清單控制件物件的`OnChildNotify`功能以及處理程式正文內來處理此消息,請檢查LVN_ODFINDITEM消息。 如果找到,則執行相應的操作。

您應該準備搜索與列表檢視控制者提供的資訊匹配的項目。 如果成功,則應返回項的索引;如果未找到匹配項,則應返回 -1。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
