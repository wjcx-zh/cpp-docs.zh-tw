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
ms.openlocfilehash: 01effb8cb1142db0bcae6f9c456e4a3b3abd69e8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269932"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

具有 Microsoft Outlook [ **巡覽窗格** ] 視覺外觀的索引標籤控制項。
如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。
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
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|將 Windows 控制項，成為新的索引標籤，在 Outlook 功能區中。|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|由架構呼叫以判斷使用者時，會出現在編輯方塊的維度會將重新命名 索引標籤。(覆寫 `CMFCBaseTabCtrl::CalcRectEdit`。)|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|若要判斷是否可以顯示較少的 Outlook 列 索引標籤上的頁面按鈕，比目前可見的調整大小作業期間，由架構呼叫。|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|若要判斷是否可以顯示更多的 Outlook 列 索引標籤上的頁面按鈕，比目前可見的調整大小作業期間，由架構呼叫。|
|[CMFCOutlookBarTabCtrl::Create](#create)|建立 Outlook 功能區 索引標籤控制項。|
|`CMFCOutlookBarTabCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|指定是否要啟用在作用中的索引標籤之間切換時，就會發生的動畫。|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|指定使用者是否可以修改索引標籤按鈕的 Outlook 功能區上的文字標籤。 (覆寫[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)。)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|由架構呼叫以啟用按鈕，可讓使用者透過 Outlook 功能區窗格上的按鈕捲動。|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|識別包含指定的點的窗格。 (覆寫[CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd)。)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|傳回 Outlook 索引標籤控制項的框線大小。|
|`CMFCOutlookBarTabCtrl::GetTabArea`|擷取的大小和位置的索引標籤控制項的索引標籤區域。 (覆寫[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)。)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|決定是否要啟用在作用中的索引標籤之間切換時，就會發生的動畫。|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|判斷 Outlook 功能區 索引標籤控制項是否以模擬 Microsoft Outlook 2003 的模式。|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|判斷點是否在索引標籤區域內。 (覆寫[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)。)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|判斷是否可以中斷連結索引標籤。 (覆寫[CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable)。)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|插入或移除工作索引標籤時，由架構呼叫。 (覆寫 `CMFCBaseTabCtrl::OnChangeTabs`。)|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|由架構呼叫以降低的索引標籤會顯示的頁面按鈕數目。|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|由架構呼叫以增加索引標籤會顯示的頁面按鈕數目。|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|顯示**瀏覽窗格選項**對話方塊。|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|重新計算索引標籤控制項的內部配置。 (覆寫[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)。)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|設定作用中的索引標籤。(覆寫[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)。)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|設定 Outlook 索引標籤控制項的框線大小。|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|設定索引標籤按鈕的 Outlook 功能區上的文字標籤的對齊方式。|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|設定包含會顯示在底部的在 Outlook 2003 模式中的 outlook 功能區的圖示點陣圖 (請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md))。|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>備註

若要建立停駐支援 outlook 功能區，請使用`CMFCOutlookBar`裝載列 索引標籤控制項 Outlook 的物件。 如需詳細資訊，請參閱 < [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

## <a name="example"></a>範例

下列範例示範如何初始化`CMFCOutlookBarTabCtrl`物件，並使用中的各種方法`CMFCOutlookBarTabCtrl`類別。 此範例示範如何啟用索引標籤頁面按鈕的 Outlook 功能區上的文字標籤就地編輯、 啟用動畫、 啟用捲軸控點，讓使用者能夠捲動按鈕在 Outlook 功能區窗格上，設定 [Outlook] 索引標籤內容的框線大小選角色，並設定上的 Outlook 功能區索引標籤按鈕的文字標籤的對齊方式。 此程式碼片段是一部分[Outlook 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxoutlookbartabctrl.h

##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl

將 Windows 控制項，成為新的索引標籤，在 Outlook 功能區中。

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
[in]指標，要加入的控制項。

*lpszName*<br/>
[in]指定索引標籤的名稱。

*bDetachable*<br/>
[in]如果為 TRUE，頁面將會建立為中斷連結。

*nImageID*<br/>
[in]在內部的映像清單中，要在新的索引標籤中顯示之影像的影像索引。

*dwControlBarStyle*<br/>
[in]指定已包裝的停駐窗格 AFX_ CBRS_ * 樣式。

### <a name="remarks"></a>備註

使用此函式將控制項加入為新的 outlook 功能區頁面。

在內部呼叫此函式[:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)。

如果您設定*bDetachable*設為 TRUE，`AddControl`會在內部建立`CDockablePaneAdapter`物件，並包裝加入的控制項。 它會自動設定的索引標籤式視窗的執行階段類別的執行階段類別`CMFCOutlookBar`和 浮動的畫面格的執行階段類別`CMultiPaneFrameWnd`。

### <a name="example"></a>範例

下列範例示範如何使用`AddControl`方法中的`CMFCOutlookBarTabCtrl`類別。 此程式碼片段是一部分[Outlook 示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

由架構呼叫期間調整大小作業，以判斷是否可以較少的 Outlook 列 索引標籤頁按鈕顯示比目前可見。

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>傳回值

如果有一個以上的按鈕;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

Outlook 功能區 索引標籤控制項以動態方式新增或移除索引標籤的顯示取決於有可用的多少空間。 架構會使用這個方法，協助該程序。

##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons

由架構呼叫期間調整大小作業，來判斷比目前可見，是否可以顯示更多的 Outlook 列 索引標籤上的頁面按鈕。

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>傳回值

如果有目前看不見; 的按鈕，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

Outlook 功能區 索引標籤控制項以動態方式新增或移除索引標籤顯示，視有可用的多少空間。 架構會使用這個方法，協助該程序。

##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create

建立 Outlook 功能區 索引標籤控制項。

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*rect*<br/>
[in]指定的初始大小和位置，像素為單位。

*pParentWnd*<br/>
[in]父視窗的點。 必須不是 NULL。

*nID*<br/>
[in]控制項 id。

### <a name="return-value"></a>傳回值

如果已順利建立控制項，非零值。否則為 0。

### <a name="remarks"></a>備註

通常，outlook 工具列索引標籤控制項時，會建立[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)控制程序的 WM_CREATE 訊息。

##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation

指定是否要啟用在作用中的索引標籤之間切換時，就會發生的動畫。

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]指定是否應該啟用或停用動畫。

### <a name="remarks"></a>備註

呼叫此函式可啟用和停用動畫。 當使用者開啟索引標籤頁時，頁面的標題投影片 增加或相應減少如果已啟用動畫。 如果動畫會停用，頁面就會變成作用中立即。

根據預設，會啟用動畫。

##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit

指定使用者是否可以修改索引標籤頁的按鈕 Outlook 功能區上的文字標籤。

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
如果為 TRUE，啟用就地編輯的文字標籤。 如果為 FALSE，停用就地編輯。

### <a name="remarks"></a>備註

呼叫此函式可啟用或停用就地編輯的索引標籤頁面按鈕上的文字標籤。 預設會停用就地編輯。

##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons

由架構呼叫以啟用 允許使用者捲動按鈕在 Outlook 功能區窗格上的捲軸控點。

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]決定是否顯示捲軸按鈕。

*bIsUp*<br/>
[in]決定是否要顯示的最上層的捲軸。

*bIsDown*<br/>
[in]決定是否要顯示底部的捲軸。

### <a name="remarks"></a>備註

啟用捲動按鈕的顯示方式。 這個方法是由架構呼叫，若要還原的捲軸按鈕的作用中的索引標籤變更時。

##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize

傳回 Outlook 索引標籤控制項的框線大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>傳回值

框線的大小，單位為像素。

##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation

指定是否要啟用在作用中的索引標籤之間切換時，就會發生的動畫。

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>傳回值

如果已啟用動畫，非零值。否則為 0。

### <a name="remarks"></a>備註

呼叫[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)函式來啟用或停用動畫。

##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003

判斷 Outlook 功能區 索引標籤控制項是否以模擬 Microsoft Outlook 2003 的模式。

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>傳回值

如果索引標籤控制項列 Outlook 為 Outlook 2003 模式，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

此值由設定[CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)。

##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

由架構呼叫以降低的索引標籤會顯示的頁面按鈕數目。

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>備註

這個方法會在重新調整控制項大小時，調整可見的頁面索引標籤按鈕數目。

##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons

由架構呼叫以增加索引標籤會顯示的頁面按鈕數目。

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>備註

這個方法會調整時控制項調整大小，會顯示的索引標籤頁面按鈕數目。

##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions

顯示**瀏覽窗格選項** 對話方塊。

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>備註

**瀏覽窗格選項**對話方塊可讓使用者選取索引標籤頁面按鈕就會顯示，並在其中顯示的順序。

由架構呼叫這個方法，是當使用者選取**瀏覽窗格選項**從控制項的自訂功能表的功能表項目。

##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab

設定作用中的索引標籤。作用中的索引標籤是已開啟，顯示其內容。

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>參數

*iTab*<br/>
[in]開啟索引標籤的以零為起始的索引。

### <a name="return-value"></a>傳回值

如果成功，開啟指定的索引標籤，非零值。否則為 0。

### <a name="remarks"></a>備註

設定作用中的索引標籤的視覺效果取決於您是否已啟用動畫。 如需詳細資訊，請參閱 < [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)。

##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize

設定 Outlook 索引標籤控制項的框線大小。

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>參數

*nBorderSize*<br/>
[in]像素為單位指定新的框線大小。

### <a name="remarks"></a>備註

設定新的框線大小並重新計算的 outlook 視窗版面配置。

##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

設定索引標籤按鈕的 Outlook 功能區上的文字標籤的對齊方式。

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*uiAlign*<br/>
[in]指定文字的對齊方式。

*bRedraw*<br/>
[in]如果為 TRUE，outlook 視窗將會重新繪製。

### <a name="remarks"></a>備註

您可以使用此函式來變更頁面按鈕的文字對齊方式。

*uiAlign*可以是下列值之一：

|常數|意義|
|--------------|-------------|
|TA_LEFT|靠左的對齊|
|TA_CENTER|置中對齊|
|TA_RIGHT|靠右對齊|

預設值是 TA_CENTER。

##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList

設定點陣圖，其中包含會顯示在底部的在 Outlook 2003 模式中的 outlook 功能區的圖示。

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>參數

*uiID*<br/>
[in]指定要載入的映像的資源識別碼。

*cx*<br/>
[in]在映像清單中，像素為單位指定影像的寬度。

*clrTransp*<br/>
[in]指定透明色彩的 RGB 值。

### <a name="return-value"></a>傳回值

如果成功則傳回 TRUE否則會傳回 FALSE。

### <a name="remarks"></a>備註

使用此函式附加影像清單的映像將會顯示在 Microsoft Office 2003 模式下的工具列按鈕。 映像索引應該對應至頁面索引。

如果不在 Microsoft Office 2003 模式中不應該呼叫這個方法。 如需詳細資訊，請參閱 < [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。

##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>參數

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)
