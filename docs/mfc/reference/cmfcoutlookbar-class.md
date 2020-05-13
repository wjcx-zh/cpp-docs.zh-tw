---
title: CMFCOutlookBar 類別
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369659"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 類別

具有 Microsoft Outlook 2000 或 Outlook 2003 [ **巡覽窗格** ] 視覺外觀的索引標籤式窗格。 該`CMFCOutlookBar`物件包含一個[CMFCOutlookBarTabCtrl 類](../../mfc/reference/cmfcoutlookbartabctrl-class.md)物件和一系列選項卡。 選項卡可以是[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)類`CWnd`物件或 派生物件。 對於使用者，Outlook 功能區會顯示為一系列按鈕與一個顯示區域。 當使用者按一下按鈕時，對應的控制項或按鈕窗格隨即顯示。

## <a name="syntax"></a>語法

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|預設建構函式。|
|`CMFCOutlookBar::~CMFCOutlookBar`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以銷毀空選項卡式窗格。 (覆寫[CBaseTabbed 窗格::允許銷毀空表板](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)窗格 。|
|[CMFCOutlookBar::接受窗格](#canacceptpane)|確定是否可以將另一個窗格停靠到 Outlook 欄窗格。 (覆蓋可停靠窗格::可接受窗格。|
|[CMFCOutlookbar::canset標題文字標籤名稱](#cansetcaptiontexttotabname)|決定選項卡式窗格的標題是否顯示與作用選項卡相同的文字。(覆寫[CBaseTabbed 窗格::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar:建立](#create)|創建 Outlook 欄控件。|
|[CMFCOutlookBar:建立自訂頁面](#createcustompage)|建立自定義 Outlook 欄選項卡。|
|`CMFCOutlookBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFC觀景欄::DoesAllowDynInsert之前](#doesallowdyninsertbefore)|確定使用者是否可以停靠Outlook欄外邊緣的控制欄。|
|[CMFCOutlookBar:浮動選項卡](#floattab)|浮動窗格,但前提是窗格當前駐留在可拆卸選項卡中。(覆蓋[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).|
|[CMFCOutlookBar:取得按鈕字型](#getbuttonsfont)|返回 Outlook 欄按鈕上文字的字體。|
|[CMFCOutlookBar:GetTabArea](#gettabarea)|返回 Outlook 欄上選項卡區域的大小和位置。 (覆寫[CBaseTabbed 窗格:取得 Tab 區域](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)。)|
|`CMFCOutlookBar::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCOutlookBar:isMode2003](#ismode2003)|確定Outlook欄的行為是否與Microsoft Office Outlook 2003的行為仿一致(請參閱備註)。|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|由[CMFCOutlookBarTabCtrl 呼叫::](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)使用動畫設定活動選項卡後設定活動選項卡。|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|由[CMFCOutlookBarTabCtrl 呼叫::](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)在使用動畫將選項卡頁設置為活動選項卡之前設置活動選項卡。|
|[CMFCOutlookBar::OnScroll](#onscroll)|如果 Outlook 欄向上或向下滾動,則由框架調用。|
|[CMFCOutlookBar:刪除自訂頁面](#removecustompage)|刪除自定義 Outlook 欄選項卡。|
|[CMFCOutlookBar::設定按鈕字型](#setbuttonsfont)|設置 Outlook 欄按鈕上的文字字型。|
|[CMFCOutlookBar:SetMode2003](#setmode2003)|指定 Outlook 欄的行為是否與 Outlook 2003 的行為仿一致(請參閱備註)。|

## <a name="remarks"></a>備註

有關 Outlook 欄的範例,請參閱[OutlookDemo 範例:MFC OutlookDemo 應用程式](../../overview/visual-cpp-samples.md)。

## <a name="implementing-the-outlook-bar"></a>實用 Outlook 列

若要在您的應用程式中使用 `CMFCOutlookBar` 控制項，請遵循下列步驟：

1. 內嵌 `CMFCOutlookBar` 物件到主框架視窗類別。

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. 在主幀中處理WM_CREATE消息時,調用[CMFCOutlookBar::創建](#create)方法來創建 Outlook 欄選項卡控制項。

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. 使用`CMFCOutlookBarTabCtrl`[CBaseTabbedPane 取得指向基礎的指標::取得基礎視窗](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)。

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. 為包含按鈕的每個選項卡創建一個[CMFCOutlookBarPane 類](../../mfc/reference/cmfcoutlookbarpane-class.md)物件。

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. 呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)以添加每個新選項卡。將*可分離*參數設置為 FALSE 以使頁面不可拆卸。 或者,使用[CMFCOutlookBarTabCtrl::添加控制](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)以添加可拆卸頁面。

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. 要將`CWnd`派生控制件(例如[CMFCShellTreeCtrl 類](../../mfc/reference/cmfcshelltreectrl-class.md))添加為選項卡,請創建控制項並調用[CMFCOutlookBarTabctrl::addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)將其添加到 Outlook 欄。

> [!NOTE]
> 您應該對每個[CMFCOutlookBarPane 類](../../mfc/reference/cmfcoutlookbarpane-class.md)`CWnd`物件和每個 派生物件使用唯一控件 ID。

在執行時動態新增或移除新頁面,請使用[CMFCOutlookBar::建立自訂頁](#createcustompage)與[CMFCOutlookBar::刪除自訂頁](#removecustompage)。

## <a name="outlook-2003-mode"></a>展望 2003 模式

在 Outlook 2003 模式下,選項卡按鈕位於 Outlook 欄窗格的底部。 當沒有足夠的空間來顯示按鈕時,它們將作為圖示顯示在窗格底部的工具列類似區域中。

使用[CMFCOutlookBar:setMode2003](#setmode2003)啟用 Outlook 2003 模式。 使用[CMFCOutlookBarTabCtrl::設定工具列圖像列表](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist)來設置包含 Outlook 欄底部顯示的圖示的點陣圖。 點陣圖中的圖示必須由選項卡索引排序。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxOutlookbar.h

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::允許銷毀空單板

指定是否可以銷毀空選項卡式窗格。

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>傳回值

如果可以銷毀空選項卡式窗格,則為 TRUE;否則,FALSE。 預設實現始終返回 TRUE。

### <a name="remarks"></a>備註

如果無法銷毀空選項卡式窗格,則框架將隱藏它。

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::接受窗格

確定是否可以將另一個窗格停靠到 Outlook 欄窗格。

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>參數

*pBar*<br/>
[在]指向另一個要停靠到此窗格的窗格的指標。

### <a name="return-value"></a>傳回值

如果另一個窗格可以停靠到 Outlook 欄窗格,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

如果 Outlook 欄處於 Outlook 2003 模式,則不支援停靠,因此返回值為 FALSE。

如果*pBar*參數為 NULL,則此方法傳回 FALSE。

否則,此方法將充當基本方法[CBasePane::canAcceptPane,](../../mfc/reference/cbasepane-class.md#canacceptpane)只不過即使未啟用停靠,Outlook 欄仍可以啟用另一個 Outlook 欄停靠在它上。

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookbar::canset標題文字標籤名稱

確定選項卡式窗格的標題是否顯示與活動選項卡相同的文本。

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>傳回值

如果 Outlook 欄標題自動設定為活動選項卡的文本,則為 TRUE;如果 Outlook 視窗標題自動設置為活動選項卡的文本,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

使用[CBaseTabbed 窗格::啟用設定標題文字標籤名稱](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)以啟用或禁用此功能。

在 Outlook 2003 模式下,此設置始終處於啟用狀態。

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar:建立

創建 Outlook 欄控件。

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>參數

*lpszCaption*<br/>
[在]指定視窗標題。

*pparentwnd*<br/>
[在]指定指向父視窗的指標。 它不得為 NULL。

*矩形*<br/>
[在]指定以像素為單位的 Outlook 欄大小和位置。

*nID*<br/>
[在]指定控制項識別碼。 必須與應用程式中使用的其他控制項指示的不同。

*dwStyle*<br/>
[在]指定所需的控制欄樣式。 有關可能的值,請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwControlBar 樣式*<br/>
[在]指定特殊庫定義的樣式。

*pContext*<br/>
[在]創建上下文。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

分兩步`CMFCOutlookBar`構造物件。 首先調用構造函數,然後調用`Create`,這將創建 Outlook 欄控件並將`CMFCOutlookBar`其附加到 物件。

請參閱[CBasePane:為](../../mfc/reference/cbasepane-class.md#createex) *dwControlBarStyle*指定的可用庫定義樣式的清單創建Ex。

### <a name="example"></a>範例

下面的示例演示如何使用`Create``CMFCOutlookBar`類的方法。 此代碼段是 Outlook[多視圖示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar:建立自訂頁面

建立自定義 Outlook 欄選項卡。

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>參數

*lpszPage 名稱*<br/>
[在]頁面標籤。

*b 啟動頁面*<br/>
[在]如果為 TRUE,則頁面在創建時變為活動狀態。

*開啟的嵌入*<br/>
[在]CBRS_ALIGN_標誌的組合,用於指定分離頁面時啟用的停靠側。

*啟用文字標籤*<br/>
[在]如果為 TRUE,則為駐留在頁面上的按鈕啟用文本標籤。

### <a name="return-value"></a>傳回值

指向新建立的頁面的指標,如果建立失敗,則指向 NULL。

### <a name="remarks"></a>備註

使用此方法使用戶能夠創建自定義 Outlook 欄頁。 每個應用程式最多可以創建 100 頁。 頁面控件指示碼從 0xF000 開始。 如果自定義 Outlook 欄頁總數超過 100,則創建將失敗。

使用[CMFCOutlookBar:刪除自定義頁面](#removecustompage)以刪除自訂頁面。

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFC觀景欄::DoesAllowDynInsert之前

指定使用者是否可以停靠 Outlook 欄外邊緣的窗格。

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

預設實現返回 FALSE。

### <a name="remarks"></a>備註

當框架查找停靠`DoesAllowDynInsertBefore`動態窗格的位置時,將調用該方法。 如果函數返回 FALSE,則框架不允許在窗格的外邊緣停靠任何動態窗格。

通常,您將創建 Outlook 欄作為靜態非浮動控制件。 您可以在派生類中重寫此函數,並返回 TRUE 以更改此行為。

> [!NOTE]
> 由於動態窗格在停靠時檢查停靠靜態窗格的狀態,因此應盡可能將動態窗格停靠在靜態窗格之後。

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar:浮動選項卡

浮動窗格。

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>參數

*pBar*<br/>
[在]指向窗格的指標以浮動。

*nTabID*<br/>
[在]要浮動的選項卡的零基索引。

*基方法*<br/>
[在]指定用於使窗格浮動的方法。  有關詳細資訊,請參閱[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。

*bHide*<br/>
[在]TRUE 以在浮動前隱藏窗格;否則,FALSE。 與此方法的基類版本不同,此參數沒有預設值。

### <a name="return-value"></a>傳回值

如果窗格浮動,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法類似於[CBaseTabbedPane::FloatTab,](../../mfc/reference/cbasetabbedpane-class.md#floattab)只不過它不允許 Outlook 欄控件上的最後一個剩餘選項卡浮動。

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar:取得按鈕字型

傳回 Outlook 欄的頁面按鈕選項卡上的文字字型。

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>傳回值

指向用於在 Outlook 欄頁按鈕選項卡上顯示文本的字型物件的指標。

### <a name="remarks"></a>備註

使用此函數可以檢索用於在Outlook頁按鈕選項卡上顯示文本的字體。 您可以透過除錯[型: 請設定 ButtonsFont](#setbuttonsfont)。

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar:GetTabArea

確定 Outlook 欄上選項卡區域的大小和位置。

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>參數

*rectTabAreaTop*<br/>
[出]當函數返回時,包含頂部選項卡區域的大小和位置(在用戶端座標中)。

*rectTab 區域底部*<br/>
[出]當函數返回時,包含底部選項卡區域的大小和位置(在用戶端座標中)。

### <a name="remarks"></a>備註

框架調用此方法以確定與目標窗格的停靠類型。 當框架確定使用者拖動窗格以停靠在目標窗格的選項卡區域時,它會嘗試將第一個窗格添加為目標窗格的新選項卡。 否則,它將嘗試將第一個窗格停靠在目標窗格的相應一側。 框架創建一個帶有滑塊的新容器,以適應其他停靠窗格。

如果 Outlook`GetTabArea`欄是靜態的,則 默認實現返回 Outlook 欄的整個工作區;如果 Outlook 欄是靜態的,則默認實現返回 Outlook 欄的整個工作區。也就是說,如果 Outlook 欄無法浮動。 否則,它將返回頁面按鈕在Outlook欄控件的頂部和底部獲取的區域。

在派生的`CMFCOutlookBar`類中重寫此方法以更改此行為。

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar:isMode2003

指定 Outlook 欄的行為是否與 Microsoft Office Outlook 2003 的行為仿一。

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>傳回值

如果 Outlook 欄在 Microsoft Office 2003 模式下運行,則非零;否則 0。

### <a name="remarks"></a>備註

您可以使用[CMFCOutlookBar::setMode2003](#setmode2003)啟用此模式。

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar:在動畫之後

由[CMFCOutlookBarTabCtrl 呼叫::](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)使用動畫設定活動選項卡後設定活動選項卡。

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>參數

*nPage*<br/>
[在]已變為活動的選項卡頁的零基索引。

### <a name="remarks"></a>備註

設置活動選項卡的視覺效果取決於是否已啟用動畫。 有關詳細資訊,請參閱[CMFCOutlookBarTabCtrl::啟用動畫](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)。

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::在動畫前打開

由[CMFCOutlookBarTabCtrl 呼叫::](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)在使用動畫將選項卡頁設置為活動選項卡之前設置活動選項卡。

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>參數

*nPage*<br/>
[在]即將設置為活動的選項卡頁的零基索引。

### <a name="return-value"></a>傳回值

如果應在設置新的活動選項卡時使用動畫,則返回 TRUE;如果應禁用動畫,則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookbar::OnScroll

如果 Outlook 欄向上或向下滾動,則由框架調用。

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>參數

*b向下*<br/>
[在]如果 Outlook 欄向下滾動,則為 TRUE;如果"Outlook"欄向上滾動,則為 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar:刪除自訂頁面

刪除自定義 Outlook 欄選項卡頁。

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>參數

*uiPage*<br/>
[在]父 Outlook 視窗中頁面的基於零的索引。

*p 目標Wnd*<br/>
[在]指標到父 Outlook 視窗。

### <a name="return-value"></a>傳回值

如果自定義頁已成功刪除,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫此函數以刪除自訂頁面。 刪除頁面時,其控制 ID 將傳回到可用 ID 池。

您必須提供指向[CMFCOutlookBarTabCtrl 類](../../mfc/reference/cmfcoutlookbartabctrl-class.md)物件的指標,其中要刪除的頁面當前駐留。 請注意,用戶可以在不同的 Outlook 欄之間移動可拆卸頁面,但有關自訂頁面的資訊位於已為其呼叫 CMFCOutlookBar 的 Outlook 欄物件中[:::創建自訂頁](#createcustompage)。

使用[CBaseTabbed 窗格:取得基礎視窗](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)以取得指向 Outlook 視窗的指標。

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::設定按鈕字型

設置 Outlook 欄按鈕上的文字字型。

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[在]指定新字型。

*bredraw*<br/>
[在]如果為 TRUE,則將重繪Outlook 欄。

### <a name="remarks"></a>備註

使用此方法可為 Outlook 選項卡頁按鈕上顯示的文本設置字型。

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar:SetMode2003

指定 Outlook 欄的行為是否與 Outlook 2003 的行為仿一。

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>參數

*bMode2003*<br/>
[在]如果為 TRUE,則啟用 Office 2003 模式。

### <a name="remarks"></a>備註

使用此函數可啟用或禁用 Office 2003 模式。 在此模式下,Outlook 欄具有附加工具列,帶有自定義按鈕。 Outlook 欄的行為符合 Microsoft Office 2003 中 Outlook 欄的行為。

默認情況下,此模式已禁用。

> [!NOTE]
> 必須在[CMFCOutlookBar:::創建](#create)之前調用此功能。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)
