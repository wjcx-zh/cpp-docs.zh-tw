---
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 309b74126f57e76aa6399f57382d88fee4400700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369668"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

具有 Microsoft Outlook [ **巡覽窗格** ] 視覺外觀的索引標籤控制項。
有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|預設建構函式。|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::添加控制](#addcontrol)|在 Outlook 欄中將 Windows 控制件添加為新選項卡。|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|由框架呼叫以確定使用者重新命名選項卡時顯示的編輯框的尺寸。 `CMFCBaseTabCtrl::CalcRectEdit`|
|[CMFCOutlookBarTabCtrl::可以顯示更少的頁面按鈕](#canshowfewerpagebuttons)|框架在調整大小操作期間調用,以確定顯示的 Outlook 欄選項卡頁按鈕是否少於當前可見按鈕。|
|[CMFCOutlookBarTabCtrl::可以顯示更多頁面按鈕](#canshowmorepagebuttons)|框架在調整大小操作期間調用,以確定顯示的 Outlook 欄選項卡頁按鈕是否比當前可見數多。|
|[CMFCOutlookBarTabCtrl::創建](#create)|建立 Outlook 欄選項卡控制項。|
|`CMFCOutlookBarTabCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCOutlookBarTabCtrl::啟用動畫](#enableanimation)|指定是否啟用活動選項卡之間切換期間發生的動畫。|
|[CMFCOutlookBartabCtrl::啟用原點編輯](#enableinplaceedit)|指定使用者是否可以修改 Outlook 欄選項卡按鈕上的文本標籤。 ( 覆寫[CMFCBaseTabctrl:啟用位置編輯](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::啟用ScrollButton](#enablescrollbuttons)|由框架呼叫以啟用允許使用者滾動流覽Outlook欄窗格上的按鈕的按鈕。|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|識別包含指定點的窗格。 (覆寫[CMFCBaseTabctrl:尋找目標](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl:取得邊界大小](#getbordersize)|返回 Outlook 選項卡控件的邊框大小。|
|`CMFCOutlookBarTabCtrl::GetTabArea`|檢索選項卡控制項的選項卡區域的大小和位置。 (覆蓋[CMFCBaseTabCtrl:getTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCOutlookBarTabCtrl::取得可見頁面按鈕](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl:動畫](#isanimation)|確定是否啟用了在活動選項卡之間切換期間發生的動畫。|
|[CMFCOutlookBarTabCtrl:isMode2003](#ismode2003)|確定Outlook欄選項卡控制項是否處於類比Microsoft Outlook 2003的模式。|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|確定點是否位於選項卡區域內。 (覆蓋[CMFCBaseTabctrl:isPtinTab 區域](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|確定選項卡是否可拆卸。 (覆寫[CMFCBaseTabCtrl:可分離的 Tab](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|插入或刪除選項卡時由框架呼叫。 (覆寫 `CMFCBaseTabCtrl::OnChangeTabs`。)|
|[CMFCOutlookBarTabCtrl::在顯示少點頁面按鈕](#onshowfewerpagebuttons)|框架調用以減少可見的選項卡頁按鈕數。|
|[CMFCOutlookBarTabCtrl::在顯示更多頁面按鈕](#onshowmorepagebuttons)|由框架調用以增加可見的選項卡頁按鈕數。|
|[CMFCOutlookBarTabCtrl::在顯示選項上](#onshowoptions)|顯示**導航窗格選項**對話方塊。|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|重新計算選項卡控制件的內部佈局。 (覆蓋[CMFCBaseTabCtrl:recalclayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::設定活動選項卡](#setactivetab)|設定作用選項卡.(覆寫[CMFCBaseTabCtrl::設定活動選項卡](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::設定邊框大小](#setbordersize)|設置Outlook選項卡控制項的邊框大小。|
|[CMFCOutlookBarTabCtrl::設定頁面按鈕文字對齊](#setpagebuttontextalign)|設置Outlook欄選項卡按鈕上文本標籤的對齊方式。|
|[CMFCOutlookBarTabCtrl::設定工具列圖片清單](#settoolbarimagelist)|設置包含 Outlook 2003 模式下 Outlook 欄底部顯示的圖示的點陣圖(請參閱[CMFCOutlookBar 類](../../mfc/reference/cmfcoutlookbar-class.md))。|
|[CMFCOutlookBarTabCtrl::設定可見頁面按鈕](#setvisiblepagebuttons)||

## <a name="remarks"></a>備註

要建立具有停靠支援的 Outlook 欄,請`CMFCOutlookBar`使用物件 承載 Outlook 欄選項卡控制項。 有關詳細資訊,請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="example"></a>範例

下面的範例展示如何初始化`CMFCOutlookBarTabCtrl`物件`CMFCOutlookBarTabCtrl`並在類中使用各種方法。 該範例展示如何在 Outlook 欄的選項卡頁按鈕上啟用文本標籤的就地編輯、啟用動畫、啟用允許使用者滾動"Outlook"欄窗格上的按鈕的滾動控點、設置 Outlook 選項卡控件的邊框大小以及設置 Outlook 欄選項卡按鈕上文本標籤的對齊方式。 此代碼段是 Outlook[演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabCtrl::添加控制

在 Outlook 欄中將 Windows 控制件添加為新選項卡。

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>參數

*pWndCtrl*<br/>
[在]指向要添加的控制項的指標。

*lpsz名稱*<br/>
[在]指定選項卡的名稱。

*b 可拆卸*<br/>
[在]如果為 TRUE,則頁面將創建為可拆卸頁面。

*nImageID*<br/>
[在]要在新選項卡中顯示的圖像的內部圖像清單中的圖像索引。

*dwControlBar 樣式*<br/>
[在]為包裝的停靠窗格指定AFX_CBRS_* 樣式。

### <a name="remarks"></a>備註

使用此函數將控制項添加為Outlook欄的新頁。

此功能在[CMFCBaseTabCtrl 上內部呼叫:AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)。

如果將*bDetach*設置為`AddControl`TRUE,`CDockablePaneAdapter`則內部創建 物件並包裝添加的控制項。 這個選項會自動設定指定的視窗的執行時類別設定到的`CMFCOutlookBar`執行時類別,將浮動的畫面的執行時類別設定`CMultiPaneFrameWnd`到 。

### <a name="example"></a>範例

下面的示例演示如何在`AddControl``CMFCOutlookBarTabCtrl`類中使用 方法。 此代碼段是 Outlook[演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::可以顯示更少的頁面按鈕

框架在調整大小操作期間調用,以確定顯示的 Outlook 欄選項卡頁按鈕是否少於當前可見按鈕。

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>傳回值

如果有多個按鈕,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

Outlook 欄選項卡控制項會根據可用空間的可用空間量動態添加或刪除顯示選項卡。 框架使用此方法來幫助該過程。

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::可以顯示更多頁面按鈕

框架在調整大小操作期間調用,以確定顯示的 Outlook 欄選項卡頁按鈕是否比當前可見數多。

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>傳回值

如果當前看不到按鈕,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

Outlook 欄選項卡控制項會根據可用空間的可用空間量動態添加或刪除選項卡。 框架使用此方法來幫助該過程。

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabCtrl::創建

建立 Outlook 欄選項卡控制項。

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]指定初始大小和位置(以像素為單位)。

*pparentwnd*<br/>
[在]指向父視窗。 不能為 NULL。

*nID*<br/>
[在]控件識別碼。

### <a name="return-value"></a>傳回值

如果控件已成功創建,則非零;否則 0。

### <a name="remarks"></a>備註

通常,當[CMFCOutlookBar 類](../../mfc/reference/cmfcoutlookbar-class.md)控制進程的WM_CREATE消息時,將創建 Outlook 欄選項卡控制件。

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabCtrl::啟用動畫

指定是否啟用活動選項卡之間切換期間發生的動畫。

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]指定是啟用還是禁用動畫。

### <a name="remarks"></a>備註

調用此函數以啟用和禁用動畫。 當使用者打開選項卡頁時,如果啟用了動畫,該頁的標題將向上或向下滑動。 如果禁用動畫,頁面將立即變為活動狀態。

默認情況下,動畫已啟用。

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBartabCtrl::啟用原點編輯

指定使用者是否可以修改 Outlook 欄選項卡頁按鈕上的文本標籤。

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
如果為 TRUE,則啟用文本標籤的就地編輯。 如果 FALSE,則禁用就地編輯。

### <a name="remarks"></a>備註

呼叫此函數以啟用或禁用選項卡頁按鈕上文本標籤的就地編輯。 默認情況下,將禁用就地編輯。

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::啟用ScrollButton

框架調用以啟用允許使用者滾動在 Outlook 欄窗格上的按鈕的滾動控點。

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]確定是否顯示滾動按鈕。

*bIsUp*<br/>
[在]確定是否顯示頂部滾動條。

*bIsDown*<br/>
[在]確定是否顯示底部滾動條。

### <a name="remarks"></a>備註

啟用滾動按鈕的顯示。 當活動選項卡更改以還原滾動按鈕時,框架將調用此方法。

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBarTabCtrl:取得邊界大小

返回 Outlook 選項卡控件的邊框大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>傳回值

邊框大小(以像素為單位)。

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::取得可見頁面按鈕

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabCtrl:動畫

指定是否啟用活動選項卡之間切換期間發生的動畫。

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>傳回值

如果啟用了動畫,則非零;否則 0。

### <a name="remarks"></a>備註

調用[CMFCOutlookBarTabCtrl::啟用動畫](#enableanimation)功能以啟用或禁用動畫。

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabCtrl:isMode2003

確定Outlook欄選項卡控制項是否處於類比Microsoft Outlook 2003的模式。

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>傳回值

如果 Outlook 欄選項卡控制項處於 Outlook 2003 模式,則為 TRUE;如果 Outlook 欄選項卡控制項處於 Outlook 2003 模式,則為 TRUE。否則 FALSE;

### <a name="remarks"></a>備註

此值由[CMFCOutlookBar 設定:setMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)。

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::在顯示少點頁面按鈕

框架調用以減少可見的選項卡頁按鈕數。

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>備註

此方法調整控制件調整大小時可見頁選項卡按鈕的數量。

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::在顯示更多頁面按鈕

由框架調用以增加可見的選項卡頁按鈕數。

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>備註

此方法調整調整控制件調整大小時可見的選項卡頁按鈕數。

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::在顯示選項上

顯示 **「導航窗格選項**」 對話框。

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>備註

**"導覽窗格選項"** 對話框允許使用者選擇要顯示的選項卡頁按鈕及其顯示順序。

當使用者從控制項的自訂選單中選擇**導航窗格選項**功能表項時,框架將調用此方法。

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBarTabCtrl::設定活動選項卡

設置活動選項卡。活動選項卡是打開的選項卡,其內容可見。

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>參數

*iTab*<br/>
[在]要打開的選項卡的零基索引。

### <a name="return-value"></a>傳回值

如果指定的選項卡已成功打開,則非零;否則 0。

### <a name="remarks"></a>備註

設置活動選項卡的視覺效果取決於是否已啟用動畫。 有關詳細資訊,請參閱[CMFCOutlookBarTabCtrl::啟用動畫](#enableanimation)。

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBarTabCtrl::設定邊框大小

設置Outlook選項卡控制項的邊框大小。

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>參數

*n邊框大小*<br/>
[在]指定以像素為單位的新邊框大小。

### <a name="remarks"></a>備註

設置新的邊框大小並重新計算 Outlook 視窗佈局。

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::設定頁面按鈕文字對齊

設置Outlook欄選項卡按鈕上文本標籤的對齊方式。

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*烏伊·馬利*<br/>
[在]指定文字對齊方式。

*bredraw*<br/>
[在]如果為 TRUE,則將重繪Outlook 視窗。

### <a name="remarks"></a>備註

使用此函數可以更改頁面按鈕的文本對齊方式。

*uiAlign*可以是以下值之一:

|持續性|意義|
|--------------|-------------|
|TA_LEFT|左對齊|
|TA_CENTER|中心對齊|
|TA_RIGHT|右對齊|

默認值為TA_CENTER。

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::設定工具列圖片清單

設置包含 Outlook 2003 模式下 Outlook 欄底部顯示的圖示的點陣圖。

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]指定要載入的影像的資源識別碼。

*殘雪*<br/>
[在]指定圖像清單中圖像的寬度(以像素為單位)。

*clrTransp*<br/>
[在]指定透明顏色的 RGB 值。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;否則返回 FALSE。

### <a name="remarks"></a>備註

使用此功能可以附加圖像清單,其圖像將在 Microsoft Office 2003 模式下顯示在工具列按鈕上。 圖像索引應對應於頁面索引。

如果不是在 Microsoft Office 2003 模式下,則不應調用此方法。 有關詳細資訊,請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::設定可見頁面按鈕

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>參數

[在]*N 可見頁面按鈕*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)
