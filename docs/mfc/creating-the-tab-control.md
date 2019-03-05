---
title: 建立索引標籤控制項
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 4627009e2e07d1c5692d83d8d6262a9fcd37977e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304908"
---
# <a name="creating-the-tab-control"></a>建立索引標籤控制項

建立索引標籤控制項的方式取決於您是在使用對話方塊中的控制項或建立在非對話方塊視窗中。

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CTabCtrl

1. 在對話方塊編輯器中，加入您的對話方塊範本資源中的索引標籤控制項。 指定其控制項 ID.

1. 使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)若要加入成員變數的型別[CTabCtrl](../mfc/reference/ctabctrl-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CTabCtrl` 成員函式。

1. 對應您要處理的任何索引標籤控制項通知訊息的對話方塊類別中的處理常式函式。 如需詳細資訊，請參閱 <<c0> [ 將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)。

1. 在  [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定樣式的`CTabCtrl`。

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>若要在非對話方塊視窗使用 CTabCtrl

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](../mfc/reference/ctabctrl-class.md#create)成員函式，可能是在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，可能是與父視窗的為早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。

之後`CTabCtrl`已建立物件，您可以設定或清除下列延伸樣式：

- **TCS_EX_FLATSEPARATORS**索引標籤控制項將會繪製索引標籤項目之間的分隔符號。 此延伸樣式，只會影響索引標籤控制項具有**TCS_BUTTONS**並**TCS_FLATBUTTONS**樣式。 根據預設，建立具有索引標籤控制項**TCS_FLATBUTTONS**樣式設定這個項目延伸樣式。

- **TCS_EX_REGISTERDROP**  索引標籤控制項產生**TCN_GETOBJECT**物件拖曳至索引標籤中的項目控制項上時，通知訊息，以要求置放目標物件。

    > [!NOTE]
    >  若要接收**TCN_GETOBJECT**通知，您必須初始化 OLE 程式庫，呼叫[AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)。

這些樣式就可以擷取和設定，控制建立之後，個別呼叫[GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle)並[SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle)成員函式。

例如，設定**TCS_EX_FLATSEPARATORS**樣式與下列程式碼行：

[!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]

清除**TCS_EX_FLATSEPARATORS**樣式從`CTabCtrl`下列幾行程式碼的物件：

[!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]

這會移除出現的按鈕之間的分隔符號您`CTabCtrl`物件。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
