---
title: TN021:命令和訊息路由
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: ce8aa2013c8f2f351ca1028f0d6103135ba5ecd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306177"
---
# <a name="tn021-command-and-message-routing"></a>TN021:命令和訊息路由

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示說明命令路由，並分派架構，以及一般視窗訊息路由中的進階的主題。

視覺效果，請參閱C++一般的詳細資料所述，在架構上特別區分 Windows 訊息、 控制通知和命令。 這個附註會假設您已非常熟悉進行列印的文件中所述的問題，並只處理非常進階的主題。

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>命令路由，並分派 MFC 1.0 功能進化到 MFC 2.0 架構

Windows 具有 WM_COMMAND 訊息是多載來提供的功能表命令、 快速鍵和對話方塊控制項告知的通知。

MFC 1.0，有點藉由使用命令處理常式 (例如，"OnFileNew 」) 內建`CWnd`衍生類別呼叫以回應特定的 WM_COMMAND。 這黏附搭配呼叫訊息對應中，資料結構，並導致空間非常有效率的命令機制。

MFC 1.0 也會提供額外的功能，來分隔命令訊息中的控制項通知。 命令會以 16 位元識別碼，有時也稱為命令識別碼。 一般而言，命令會開始從`CFrameWnd`（也就是功能表中，選取或翻譯的加速器） 和路由傳送至各種不同的其他視窗。

MFC 1.0 使用的有限的意義上實作的多個文件介面 (MDI) 的命令路由。 （MDI 框架視窗會委派至其作用中的 MDI 子視窗的命令）。

這項功能已一般化並擴充 MFC 2.0，以允許由更廣泛的物件 （不只是視窗物件） 的命令。 它提供更多的正式和可延伸的架構，以路由訊息，並重複使用的命令目標，路由不只處理的命令，但也以反映目前的命令更新 UI 物件 （例如功能表項目和工具列按鈕）.

## <a name="command-ids"></a>命令 ID

請參閱 VisualC++如需說明路由與繫結程序的命令。 [技術提示 20](../mfc/tn020-id-naming-and-numbering-conventions.md)包含識別碼命名的相關資訊。

我們可以使用一般的前置詞"ID_"命令識別碼。 命令 Id 是 > = 0x8000。 訊息列或狀態列會顯示命令描述字串是否有 STRINGTABLE 資源具有相同識別碼的命令識別碼。

在您的應用程式的資源，命令識別碼可以出現在幾個地方：

- 在某個 STRINGTABLE 資源中，會有在訊息列提示字元相同的識別碼。

- 可能是許多功能表資源中附加至叫用相同的命令的功能表項目。

- （進階） 對話方塊按鈕 GOSUB 命令中。

在您的應用程式的原始程式碼，識別碼可以命令會出現在幾個地方：

- 在您的資源。H （或其他主要的符號標頭檔） 來定義應用程式特有的命令識別碼。

- 也許在 ID 陣列，用來建立工具列。

- 在 ON_COMMAND 巨集。

- 或許在 ON_UPDATE_COMMAND_UI 巨集。

目前，唯一需要的命令 Id 的 MFC 中實作的是 > = 0x8000 是 GOSUB 對話方塊或命令的實作。

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>使用對話方塊中的命令架構的 GOSUB 命令

路由並啟用命令的命令架構的運作方式與框架視窗、 功能表項目、 工具列按鈕、 對話方塊列按鈕、 其他控制列和其他設計用來更新需求和路由命令或控制項 Id 加入至 main 的使用者介面項目命令目標 （通常是主框架視窗）。 主要的命令目標可能會視需要的其他命令目標物件路由命令或控制項通知。

（強制回應或非強制回應） 的對話方塊可受益於某些命令架構的功能如果您將對話方塊控制項的控制項 ID 指派給適當的命令識別碼。 因此您可能需要撰寫一些額外的程式碼，不是自動的對話方塊的支援。

請注意，所有這些功能才能正常運作，您的命令 Id 應該是 > = 0x8000。 由於許多對話方塊無法路由傳送至同一個框架，共用的命令應該是 > = 0x8000，而在特定的對話方塊中的非共用的 IDCs 應該是 < = 0x7FFF。

您可以將一般按鈕放，一般的強制回應對話方塊，並設定為適當的命令 id。 按鈕的 IDC 當使用者選取按鈕時，對話方塊 （通常是主框架視窗） 的擁有者會取得命令，就像任何其他命令。 這就稱為 GOSUB 命令，因為它通常用來顯示其他對話方塊 (GOSUB 的第一個對話方塊)。

您也可以呼叫此函式`CWnd::UpdateDialogControls`上您的對話方塊，並傳遞您的主框架視窗的位址。 此函式將會啟用或停用您根據它們是否具有命令處理常式在框架中的對話方塊控制項。 會呼叫此函數會自動為您的控制列，在您的應用程式閒置迴圈中，但您必須針對您想要讓這項功能的一般對話方塊的直接呼叫它。

## <a name="when-onupdatecommandui-is-called"></a>ON_UPDATE_COMMAND_UI 呼叫時

維護啟用/已核取狀態的所有程式 功能表項目所有的時間，可能會耗費大量運算資源的問題。 啟用/核取功能表項目只有在使用者選取快顯視窗時，才是常用的技巧。 MFC 2.0 實作`CFrameWnd`WM_INITMENUPOPUP 訊息的處理，並使用命令路由架構決定功能表透過 ON_UPDATE_COMMAND_UI 處理常式的狀態。

`CFrameWnd` 也會處理 WM_ENTERIDLE 訊息來描述在目前的功能表，選取狀態列的 （也稱為訊息列） 的項目。

編輯視覺效果的應用程式的功能表結構C++，用來代表潛在 WM_INITMENUPOPUP 次可用的命令。 ON_UPDATE_COMMAND_UI 處理常式可以修改的狀態或文字的功能表，或如 （例如檔案 MRU 清單或 OLE 動詞命令的快顯功能表） 的進階用法，實際修改功能表結構 功能表繪製前。

ON_UPDATE_COMMAND_UI 處理同一種為了工具列 （和其他控制項列） 應用程式時進入其閒置迴圈。 請參閱*類別庫參考*並[技術提示 31](../mfc/tn031-control-bars.md)如需有關控制列。

## <a name="nested-pop-up-menus"></a>巢狀的快顯功能表

如果您使用巢狀的功能表結構，您會發現，在兩個不同的情況下，會呼叫 ON_UPDATE_COMMAND_UI 處理常式，如快顯功能表中的第一個功能表項目。

首先，它會呼叫本身的快顯功能表。 這是必要的因為快顯功能表中沒有識別碼，我們使用的快顯功能表的第一個功能表項目識別碼來參考整個快顯功能表。 在此情況下， *m_pSubMenu*成員變數`CCmdUI`物件將為非 NULL，並將指向的快顯功能表。

第二，它會呼叫之前所要繪製的快顯功能表中的功能表項目。 在此情況下，識別碼是指只是第一個功能表項目和*m_pSubMenu*成員變數`CCmdUI`物件將會是 NULL。

這可讓您啟用快顯功能表區別其功能表項目，但您必須撰寫一些功能表感知程式碼。 例如，在具有下列結構的巢狀功能表：

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

ID_NEW_SHEET 和 ID_NEW_CHART 命令可以個別啟用或停用。 **新增**應該啟用快顯功能表，如果其中一種已啟用。

ID_NEW_SHEET （快顯視窗中的第一個命令） 的命令處理常式會看起來像：

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

ID_NEW_CHART 的命令處理常式會是一般更新命令處理常式和類似的外觀：

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="oncommand-and-onbnclicked"></a>ON_COMMAND 和 ON_BN_CLICKED

訊息對應巨集，如**ON_COMMAND**並**ON_BN_CLICKED**都相同。 MFC 命令和控制通知路由機制只會使用的命令 ID 來決定路由傳送至的位置。 控制使用通知控制通知碼為零 (**BN_CLICKED**) 解譯為命令。

> [!NOTE]
> 事實上，所有的控制項通知訊息會通過命令處理常式鏈結。 比方說，就技術上可行，您可以撰寫的控制項告知處理常式**EN_CHANGE**文件類別中。 這是功能的不一般建議，因為實際的應用程式，這項功能很少、 ClassWizard，不支援的功能和使用可能會導致易損壞的程式碼。

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>停用按鈕控制項的自動停用

如果您放置對話方塊列上的按鈕控制項，或使用 where 對話方塊中，您要呼叫**CWnd::UpdateDialogControls**自己，您會注意到該按鈕，並沒有**ON_COMMAND** 或**ON_UPDATE_COMMAND_UI**處理常式將會自動停用您的架構。 在某些情況下，您不需要有處理常式，但您會想要持續啟用按鈕。 若要這麼做最簡單方式是將空的命令處理常式 （簡單與 ClassWizard） 和不在其中執行任何動作。

## <a name="window-message-routing"></a>視窗訊息路由

以下會說明一些更進階的主題上的 MFC 類別，以及它們如何影響 Windows 訊息路由和其他主題。 此處提供的資訊只簡短描述。 請參閱*類別庫參考*公用 Api 的詳細資料。 請參閱 MFC 程式庫原始程式碼，如需有關實作詳細資料。

請參閱[技術的附註 17](../mfc/tn017-destroying-window-objects.md)視窗中清除的詳細資訊，非常重要的主題針對所有**CWnd**-衍生的類別。

## <a name="cwnd-issues"></a>CWnd 問題

實作成員函式**On_xxx_reflect**提供一種功能強大且可擴充的架構，用於連結或否則通知的訊息、 命令和控制項的子視窗 （也稱為控制項）請移至其父代 （或 「 擁有者 」） 的通知。 如果子視窗 （/ 控制） 是C++ **CWnd**物件本身，虛擬函式**OnChildNotify**稱為第一次使用的參數從原始訊息 (也就是**訊息**結構)。 子視窗可以單獨將訊息、 吃下它，或修改父 （罕見） 的訊息。

預設值**CWnd**實作會處理下列訊息，並使用**OnChildNotify**攔截程序，讓子視窗 （控制項） 在訊息的第一次存取：

- **WM_MEASUREITEM**並**WM_DRAWITEM** （的自繪）

- **WM_COMPAREITEM**並**WM_DELETEITEM** （的自繪）

- **時傳遞 WM_HSCROLL**和**WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

您會發現**OnChildNotify**攔截程序用來變更成自繪訊息的主控描繪訊息。

除了**OnChildNotify**攔截程序捲動訊息有進一步的路由行為。 如需捲軸及來源的詳細資訊請參閱下方**時傳遞 WM_HSCROLL**並**WM_VSCROLL**訊息。

## <a name="cframewnd-issues"></a>CFrameWnd 問題

**CFrameWnd**類別提供的大部分命令路由和使用者介面更新實作。 這主要用於應用程式的主框架視窗 (**M_pmainwnd**)，但適用於所有框架視窗。

主框架視窗是使用功能表列的視窗和 [狀態] 列的父系或訊息列。 請參閱上述的討論內容，在命令路由和**WM_INITMENUPOPUP。**

**CFrameWnd**類別提供管理功能的作用中的檢視。 下列訊息會路由傳送到現用檢視表：

- （使用中的檢視會取得它們的第一次存取） 的所有命令訊息。

- **時傳遞 WM_HSCROLL**並**WM_VSCROLL**來自同層級捲軸 （如下所示）。

- **WM_ACTIVATE** (與**WM_MDIACTIVATE** mdi) 取得轉換成虛擬函式呼叫**CView::OnActivateView**。

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd 問題

這兩個 MDI 框架視窗類別衍生自**CFrameWnd**同時啟用相同的命令路由排序因此和使用者介面更新中提供**CFrameWnd**。 在典型的 MDI 應用程式，只在主框架視窗 (也就是**CMDIFrameWnd**物件) 保留在功能表列和狀態列，因此命令路由實作的主要來源。

一般路由的配置是現用的 MDI 子視窗取得命令的第一次存取。 預設值**PreTranslateMessage**函式中處理這兩個 MDI 子視窗的快速鍵對應表 （第一次） 和 MDI 框架 （第二個） 以及通常由標準 MDI 系統命令加速器**TranslateMDISysAccel** （最後一個）。

## <a name="scroll-bar-issues"></a>捲軸的問題

處理捲動訊息時 (**時傳遞 WM_HSCROLL**/**OnHScroll**及/或**WM_VSCROLL**/**OnVScroll**)，您應該嘗試寫入處理常式程式碼，因此它不會依賴捲軸列訊息的來源。 這不只是一般的 Windows 問題，因為捲動訊息可能來自，則為 true 的捲軸控制項，或從**WS_HSCROLL**/**WS_VSCROLL**捲軸不是捲軸控制項。

MFC 擴充，讓子系或同層級項目正在捲動視窗的捲軸控制項 （事實上，捲軸和要捲動的視窗之間的父子式關聯性可以是任何項目）。 這是特別重要的分隔視窗具有共用的捲軸。 請參閱[技術的附註 29](../mfc/tn029-splitter-windows.md)如需實作詳細資料**CSplitterWnd**包括的詳細資訊，在共用的捲軸列的問題。

附帶一提，在有兩個**CWnd**衍生的類別，在指定捲軸樣式建立的時間會截取並不會傳遞給 Windows。 建立常式，傳遞**WS_HSCROLL**並**WS_VSCROLL**可以獨立設定，但之後無法變更建立。 當然，您應該不是直接測試，或設定他們所建立之視窗的 WS_SCROLL 樣式位元。

針對**CMDIFrameWnd**捲軸樣式您傳遞給**建立**或是**LoadFrame**用來建立 MDICLIENT。 如果您想要的是可捲動的 MDICLIENT 區域 （例如 Windows 程式經理） 務必設定兩者捲軸樣式 (**WS_HSCROLL** &#124; **WS_VSCROLL**) 用來建立樣式**CMDIFrameWnd**。

針對**CSplitterWnd**捲軸樣式套用至特殊的共用的捲軸的分隔器區域。 對於靜態分隔視窗，您通常不會設定任一捲軸樣式。 動態分隔視窗中，您通常必須捲軸樣式集，您將分割，也就是方向**WS_HSCROLL**您可以將分割的資料列，如果**WS_VSCROLL**可以分割資料行。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
