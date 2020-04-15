---
title: TN021：命令和訊息路由
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370401"
---
# <a name="tn021-command-and-message-routing"></a>TN021：命令和訊息路由

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本說明描述了命令路由和調度體系結構以及常規視窗消息路由中的高級主題。

有關此處描述的體系結構的一般詳細資訊,請參閱 Visual C++,特別是 Windows 消息、控件通知和命令之間的區別。 本說明假定您非常熟悉列印文檔中描述的問題,並且僅涉及非常高級的主題。

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>命令路由和調度 MFC 1.0 功能演變為 MFC 2.0 體系結構

Windows 具有已重載入WM_COMMAND訊息,以提供功能表命令、快速鍵和對話方塊控制通知的通知。

MFC 1.0`CWnd`通過允許 派生類中的命令處理程式(例如"OnFileNew")調用以回應特定WM_COMMAND,從而在此基礎上構建了一點。 這與稱為消息映射的數據結構粘合在一起,併產生了非常節省空間的命令機制。

MFC 1.0 還提供了用於將控制通知與命令消息分開的其他功能。 命令由 16 位 ID 表示,有時稱為命令 ID。 命令通常從(`CFrameWnd`即選單選擇或翻譯的加速器) 開始,並路由到各種其他視窗。

MFC 1.0 在有限意義上使用命令路由,用於實現多文檔介面 (MDI)。 (MDI 框架視窗將命令委託給其活動 MDI 子視窗。

此功能已在 MFC 2.0 中進行推廣和擴展,以允許由更廣泛的物件(而不僅僅是視窗物件)處理命令。 它為路由消息提供了更正式和可擴展的體系結構,並重用命令目標路由,不僅用於處理命令,還用於更新 UI 物件(如功能表項和工具列按鈕),以反映命令的當前可用性。

## <a name="command-ids"></a>命令 ID

有關命令路由和綁定過程的說明,請參閱可視化C++。 [技術說明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)包含有關 ID 命名的資訊。

我們使用通用首碼"ID_"用於命令 ID。 命令 ID >= 0x8000。 如果存在與命令 ID 具有相同 ID 的 STRINGTABLE 資源,則消息行或狀態列將顯示命令描述字串。

在應用程式的資源中,命令 ID 可以出現在多個位置:

- 在一個與消息列提示具有相同 ID 的 STRINGTABLE 資源中。

- 在可能附加到調用同一命令的功能表項的許多 MENU 資源中。

- (ADVANCED)在 GOSUB 命令的對話框按鈕中。

在應用程式的原始碼中,命令 ID 可以出現在多個位置:

- 在你的資源中。H(或其他主符號標頭檔)用於定義特定於應用程式的命令指示。

- 用於建立工具列的 ID 陣列中。

- 在ON_COMMAND宏中。

- 在ON_UPDATE_COMMAND_UI宏中。

目前,MFC 中唯一需要命令 ID >= 0x8000 的實現是 GOSUB 對話方塊/命令的實現。

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB 指令,在對話框中使用命令體系結構

路由和啟用命令的命令體系結構非常適合框架視窗、功能表項、工具列按鈕、對話框列按鈕、其他控制欄和其他使用者介面元素,這些元素旨在按需更新命令或控制指示到主命令目標(通常是主框架視窗)。 該主命令目標可以根據需要將命令或控制通知路由到其他命令目標物件。

如果將對話方塊控制件的控制 ID 分配給相應的命令 ID,則對話方塊(模式或無模式)可以從命令體系結構的某些功能中受益。 對對話框的支援不是自動的,因此您可能需要編寫一些附加代碼。

請注意,要使所有這些功能正常工作,命令 ID 應>= 0x8000。 由於許多對話框可以路由到同一幀,因此共用命令應>= 0x8000,而特定對話方塊中的非共用 IDC 應<= 0x7FFF。

您可以將普通按鈕放在正常模式對話框中,將按鈕的 IDC 設定為相應的命令 ID。 當用戶選擇該按鈕時,對話框的所有者(通常是主框架視窗)將像任何其他命令一樣獲取該命令。 這稱為 GOSUB 命令,因為它通常用於啟動另一個對話方塊(第一個對話框的 GOSUB)。

您還可以在對話框上調用該`CWnd::UpdateDialogControls`函數,並將其傳遞給主框架視窗的位址。 此函數將根據對話方塊控制程式在幀中是否具有命令處理程式啟用或禁用它們。 對於應用程式空閒迴圈中的控制欄,將自動調用此功能,但您必須直接調用它,用於希望具有此功能的正常對話方塊。

## <a name="when-on_update_command_ui-is-called"></a>呼叫ON_UPDATE_COMMAND_UI時

始終保持程式功能表項的所有啟用/檢查狀態可能是計算上成本高昂的問題。 一種常見技術是僅在使用者選擇 POPUP 時啟用/檢查功能表項。 mFC 2.0`CFrameWnd`的 實現處理WM_INITMENUPOPUP消息,並使用命令路由體系結構通過ON_UPDATE_COMMAND_UI處理程序確定功能表狀態。

`CFrameWnd`還處理WM_ENTERIDLE消息來描述在狀態列(也稱為消息行)上選擇的當前功能表項。

由 Visual C++ 編輯的應用程式功能表結構用於表示WM_INITMENUPOPUP時可用的潛在命令。 ON_UPDATE_COMMAND_UI處理程式可以修改選單的狀態或文本,或用於高級用途(如檔 MRU 清單或 OLE Verbs 彈出式功能表),在繪製選單之前實際修改功能表結構。

當應用程式進入空閒迴圈時,對工具列(和其他控制欄)執行相同的ON_UPDATE_COMMAND_UI處理。 有關控制欄的詳細資訊,請參閱*類庫參考*[和技術說明 31。](../mfc/tn031-control-bars.md)

## <a name="nested-pop-up-menus"></a>巢狀彈出式選單

如果使用嵌套功能表結構,您會注意到在兩個不同的情況下調用彈出功能表中第一個功能表項ON_UPDATE_COMMAND_UI處理程式。

首先,它調用彈出功能表本身。 這是必要的,因為彈出式功能表沒有 ID,我們使用彈出式功能表的第一個功能表項的 ID 來引用整個彈出式功能表。 在這種情況下,`CCmdUI`物件的*m_pSubMenu*成員變數將為非 NULL,並將指向彈出功能表。

其次,在繪製彈出式功能表中的功能表項之前調用它。 在這種情況下,ID 僅引用第一個功能表項`CCmdUI`, 物件*m_pSubMenu*成員變數將為 NULL。

這允許您啟用不同於其功能表項的彈出式功能表,但需要編寫一些功能表感知代碼。 例如,在具有以下結構的嵌套功能表中:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

可以獨立啟用或禁用ID_NEW_SHEET和ID_NEW_CHART命令。 如果啟用了兩個中的一個,則應啟用 **"新建**"彈出式功能表。

ID_NEW_SHEET的命令處理程式(彈出視窗中的第一個命令)如下所示:

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

ID_NEW_CHART的命令處理程式將是一個正常的更新命令處理程式,如下所示:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND和ON_BN_CLICKED

**ON_COMMAND**和**ON_BN_CLICKED**的消息映射宏相同。 MFC 命令和控制通知路由機制僅使用命令 ID 來決定路由到何處。 控制項通知代碼為零 **(BN_CLICKED**) 的控制項通知被解釋為命令。

> [!NOTE]
> 事實上,所有控件通知消息都通過命令處理程序鏈。 例如,從技術上講,您可以在文檔類中為**EN_CHANGE**編寫控件通知處理程式。 這通常不可取,因為此功能的實際應用很少,ClassWizard 不支援該功能,並且使用該功能可能會導致代碼脆弱。

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>關閉自動關閉按鈕控制項

如果在對話方塊列或使用您自己調用**CWnd::UpdateDialogControls**的對話框中放置按鈕控制項,您會注意到框架會自動為您禁用沒有**ON_COMMAND**或**ON_UPDATE_COMMAND_UI**處理程式的按鈕。 在某些情況下,您不需要有處理程式,但您希望該按鈕保持啟用狀態。 實現此目的的最簡單方法是添加虛擬命令處理程式(易於使用 ClassWizard),並且不執行任何操作。

## <a name="window-message-routing"></a>視窗訊息路由

下面介紹了 MFC 類上的一些更高級的主題,以及 Windows 消息路由和其他主題如何影響它們。 此處的資訊僅簡要描述。 有關公共 API 的詳細資訊,請參閱*類別庫參考*。 有關實現詳細資訊的詳細資訊,請參閱 MFC 庫原始程式碼。

有關視窗清理的詳細資訊,請參閱[技術說明 17,](../mfc/tn017-destroying-window-objects.md)這是所有**CWnd**派生類的一個非常重要的主題。

## <a name="cwnd-issues"></a>問題

實現成員函數**CWnd::OnChildNotify**為子視窗(也稱為控件)提供了一個強大且可擴展的體系結構,用於鉤住或以其他方式通知發送到其父級(或"擁有者")的消息、命令和控制通知。 如果子視窗(/控件)是**cWnd**物件本身C++,則首先使用原始消息(即**MSG**結構)中的參數調用虛擬函數**OnChildNotify。** 子視窗可以單獨保留消息、食用郵件或修改父級的消息(罕見)。

預設**的 CWnd**實現處理以下訊息,並使用**OnChildNotify**掛鈎允許子視窗(控制件)首先存取消息:

- **WM_MEASUREITEM**與**WM_DRAWITEM(** 用於自繪 )

- **WM_COMPAREITEM**與**WM_DELETEITEM(** 用於自繪 )

- **WM_HSCROLL**和**WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

您會注意到**OnChildNotify**挂鉤用於將擁有者繪製消息更改為自製消息。

除了**OnChildNotify**掛鈎之外,滾動消息還有進一步的路由行為。 有關滾動條以及**WM_HSCROLL**和**WM_VSCROLL**消息源的更多詳細資訊,請參閱下文。

## <a name="cframewnd-issues"></a>CFramewnd 問題

**CFrameWnd**類提供大部分命令路由和使用者介面更新實現。 這主要用於應用程式的主框架視窗 (**CWinApp::m_pMainWnd**),但適用於所有框架視窗。

主框架視窗是帶有功能表欄的視窗,是狀態列或消息行的父級。 請參閱上述有關命令路由和**WM_INITMENUPOPUP的討論。**

**CFrameWnd**類提供活動檢視的管理。 以下訊息通過活動檢視路由:

- 所有命令消息(活動檢視將首先訪問它們)。

- **來自**同級滾動條WM_HSCROLL和**WM_VSCROLL**消息(見下文)。

- **WM_ACTIVATE(** 與**MDI 的WM_MDIACTIVATE)** 轉換為對虛擬函數**CView 的呼叫:onActivateView**。

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFramewnd/CMDIChildwnd 問題

兩個 MDI 幀視窗類都派生自**CFrameWnd,** 因此都啟用了相同的命令路由和用戶介面更新在**CFrameWnd**中提供。 在典型的 MDI 應用程式中,只有主框架視窗(即**CMDIFrameWnd**物件)保存功能表欄和狀態列,因此是命令路由實現的主要來源。

常規路由方案是活動 MDI 子視窗首先訪問命令。 預設**PreTranslateMessage**函數可處理 MDI 子視窗(第一個)和 MDI 幀(第二個)以及通常由**TranslateMDISysAccel(** 最後)處理的標準 MDI 系統命令加速器的加速器表。

## <a name="scroll-bar-issues"></a>捲動條問題

處理滾動訊息時 **(WM_HSCROLL**/**OnHScroll**和/或**WM_VSCROLL**/**OnVScroll),** 應嘗試編寫處理程式代碼,以便它不依賴於滾動條消息的來龍去向。 這不僅是一般 Windows 問題,因為滾動消息可能來自真正的滾動條控/件或**WS_HSCROLLWS_VSCROLL**滾動條**WS_HSCROLL**(不是滾動條控件)。

MFC 擴展了該控件,以使滾動條控件可以是要滾動的視窗的子控制件或同級控制件(事實上,滾動條和要滾動的視窗之間的父/子關係可以是任何)。 對於具有拆分視窗的共用滾動條,這一點尤其重要。 有關**CSplitterWnd**實施的詳細資訊,請參閱[技術說明 29,](../mfc/tn029-splitter-windows.md)包括有關共用滾動條問題的詳細資訊。

在旁注中,有兩個**CWnd**派生類,其中在創建時指定的滾動條樣式被困,不會傳遞到Windows。 當傳遞到建立例程時,可以獨立設置**WS_HSCROLL**和**WS_VSCROLL,** 但在創建後無法更改。 當然,不應直接測試或設置它們創建的視窗的WS_SCROLL樣式位。

對於**CMDIFrame,** 您傳遞給 **「建立**」或 **「載入幀」** 的滾動條樣式用於創建 MDICLIENT。 如果您希望有一個可滾動的 MDICLIENT 區域(如 Windows 程式管理器),請確保為用於創建**CMDIFrameWnd**的樣式設置滾動條樣式 **(WS_HSCROLL&#124;WS_VSCROLL)。** **WS_VSCROLL**

對於**CSplitterWnd,** 滾動條樣式適用於拆分器區域的特殊共用滾動條。 對於靜態拆分視窗,通常不會設置任一滾動條樣式。 對於動態拆分視窗,通常為要拆分的方向設置了滾動條樣式,也就是說,如果可以拆分行 **,WS_HSCROLL,WS_VSCROLL****拆分**列。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
