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
ms.openlocfilehash: 6d5aa6873966ecb4c845f1c503b24c07b6c0c7a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619613"
---
# <a name="creating-the-tab-control"></a>建立索引標籤控制項

建立索引標籤控制項的方式，取決於您是使用對話方塊中的控制項，還是在非對話方塊視窗中建立它。

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>直接在對話方塊中使用 CTabCtrl

1. 在對話方塊編輯器中，將 [選項卡] 控制項加入至對話方塊範本資源。 指定其控制項 ID.

1. 使用 [[加入成員變數] Wizard](../ide/adding-a-member-variable-visual-cpp.md) ，以控制項屬性加入[CTabCtrl](reference/ctabctrl-class.md)類型的成員變數。 您可以使用這個成員呼叫 `CTabCtrl` 成員函式。

1. 針對您需要處理的任何索引標籤控制項通知訊息，在對話方塊類別中對應處理常式函式。 如需詳細資訊，請參閱[將訊息對應至](reference/mapping-messages-to-functions.md)函式。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，設定的樣式 `CTabCtrl` 。

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>在非對話方塊視窗中使用 CTabCtrl

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](reference/ctabctrl-class.md#create)成員函式（可能是在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中），可能早于父視窗的[OnCreate](reference/cwnd-class.md#oncreate)處理函式（如果您要將控制項子類別化）。 設定控制項的樣式。

`CTabCtrl`建立物件之後，您可以設定或清除下列擴充樣式：

- **TCS_EX_FLATSEPARATORS**索引標籤控制項將會在索引標籤專案之間繪製分隔符號。 這個擴充樣式只會影響具有 [ **TCS_BUTTONS** ] 和 [ **TCS_FLATBUTTONS** ] 樣式的索引標籤控制項。 根據預設，建立具有**TCS_FLATBUTTONS**樣式的索引標籤控制項，會設定此延伸樣式。

- **TCS_EX_REGISTERDROP**當物件拖曳至控制項中的索引標籤專案上方時，索引標籤控制項會產生**TCN_GETOBJECT**通知訊息來要求卸載目標物件。

    > [!NOTE]
    >  若要接收**TCN_GETOBJECT**通知，您必須呼叫[AFXOLEINIT](reference/ole-initialization.md#afxoleinit)來初始化 OLE 程式庫。

在建立控制項之後，您可以使用[GetExtendedStyle](reference/ctabctrl-class.md#getextendedstyle)和[SetExtendedStyle](reference/ctabctrl-class.md#setextendedstyle)成員函式的個別呼叫，來抓取和設定這些樣式。

例如，使用下列程式程式碼來設定**TCS_EX_FLATSEPARATORS**樣式：

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

使用下列幾行程式碼，從物件中清除**TCS_EX_FLATSEPARATORS**樣式 `CTabCtrl` ：

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

這會移除在物件的按鈕之間出現的分隔符號 `CTabCtrl` 。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](using-ctabctrl.md)<br/>
[控制項](controls-mfc.md)
