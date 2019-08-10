---
title: CPaneDivider 類別
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: d4888fbf2a95652b0a38adc8ecd059a7515636cb
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866120"
---
# <a name="cpanedivider-class"></a>CPaneDivider 類別

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

`CPaneDivider`類別會分割兩個窗格, 將兩個窗格群組分割, 或將一組窗格與主框架視窗的工作區隔開。

## <a name="syntax"></a>語法

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(覆寫[CBasePane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(覆寫[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)。)|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(覆寫[CBasePane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(覆寫[CBasePane:: IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode)。)|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(覆寫[CBasePane:: IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal)。)|
|[CPaneDivider::Move](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider::Serialize](#serialize)|(覆寫 `CBasePane::Serialize`。)|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider::ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|傳回位於[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)中的窗格清單。 只有在預設窗格分隔處, 才應該呼叫這個方法。|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|傳回位於[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)中的窗格分隔清單。 只有在預設窗格分隔處, 才應該呼叫這個方法。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|指定應用程式中所有窗格分隔線的預設寬度 (以圖元為單位)。|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|保存有關`CPaneDivider`衍生物件的執行時間類別資訊的指標。|

## <a name="remarks"></a>備註

當窗格停`CPaneDivider`駐時, 架構會自動建立物件。

有兩種類型的窗格分隔線:

- 當窗格群組停駐于主框架視窗的側邊時, 會建立預設窗格分隔線。 預設窗格分隔器會保存[CPaneContainerManager 類別](../../mfc/reference/cpanecontainermanager-class.md)的指標, 並將窗格群組上大部分的作業 (例如調整窗格大小或停駐另一個窗格或容器) 重新導向至容器管理員。 每個停駐窗格都會維護其預設窗格分割線的指標。

- 一般窗格分割線只會將兩個窗格分成一個容器。 如需詳細資訊, 請參閱[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)。

## <a name="example"></a>範例

下列範例示範如何從 `CWorkspaceBar` 物件取得 `CPaneDivider` 物件。 此程式碼片段是 MDI 索引標籤[示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>需求

**標頭:** afxPaneDivider。h

##  <a name="setautohidemode"></a>CPaneDivider::SetAutoHideMode

```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>參數

在*bMode*<br/>

### <a name="remarks"></a>備註

##  <a name="setpanecontainermanager"></a>CPaneDivider::SetPaneContainerManager

```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>參數

[in] *p*<br/>

### <a name="remarks"></a>備註

##  <a name="addpane"></a>CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

在*pBar*<br/>

### <a name="remarks"></a>備註

##  <a name="addpanecontainer"></a>CPaneDivider::AddPaneContainer

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>參數

[in] *barContainerManager*<br/>
在*bOuterEdge*<br/>
[in] *pTargetBar*<br/>
在*dwAlignment*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="addrecentpane"></a>CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

在*pBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="calcexpecteddockedrect"></a>CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>參數

[in] *pWndToDock*<br/>
在*ptMouse*<br/>
在*rectResult*<br/>
[in] *bDrawTab*<br/>
[in] *ppTargetBar*<br/>

### <a name="remarks"></a>備註

##  <a name="calcfixedlayout"></a>CPaneDivider::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

在*bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="checkvisibility"></a>CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="cpanedivider"></a>CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>參數

[in] *bDefaultSlider*<br/>
[in] *pParent*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="createex"></a>CPaneDivider:: CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>參數

在*dwStyleEx*<br/>
在*dwStyle*<br/>
在*rect*<br/>
[in] *pParentWnd*<br/>
在*nID*<br/>
在*pCoNtext*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="doesallowdyninsertbefore"></a>CPaneDivider::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="doescontainfloatingpane"></a>CPaneDivider::D oesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="findpanecontainer"></a>CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>參數

在*pBar*<br/>
[in] *bLeftBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="findtabbedpane"></a>CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>參數

在*nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getdefaultwidth"></a>CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getfirstpane"></a>CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanedividers"></a>CPaneDivider::GetPaneDividers

傳回位於[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)中的窗格分隔清單。 只有在預設窗格分隔處, 才應該呼叫這個方法。

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>參數

*lstSliders*<br/>
脫銷包含位於窗格容器中的窗格分隔清單。

### <a name="remarks"></a>備註

只有針對預設窗格分隔值, 才應該呼叫這個方法。 預設窗格分割線是調整整個窗格容器大小的分隔線。

##  <a name="getpanedividerstyle"></a>CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getpanes"></a>CPaneDivider::GetPanes

傳回位於[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)中的窗格清單。 這個方法應該只呼叫來抓取預設窗格分隔線。

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>參數

*lstBars*<br/>
脫銷包含位於窗格容器中的窗格清單。

### <a name="remarks"></a>備註

只有針對預設窗格分隔值, 才應該呼叫這個方法。 預設窗格分割線是調整整個窗格容器大小的分隔線。

##  <a name="getrootcontainerrect"></a>CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getwidth"></a>CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="init"></a>CPaneDivider:: Init

```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>參數

[in] *bDefaultSlider*<br/>
[in] *pParent*<br/>

### <a name="remarks"></a>備註

##  <a name="insertpane"></a>CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

[in] *pBarToInsert*<br/>
[in] *pTargetBar*<br/>
在*dwAlignment*<br/>
[in] *lpRect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isautohidemode"></a>CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isdefault"></a>CPaneDivider:: IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ishorizontal"></a>CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="m_ndefaultwidth"></a>CPaneDivider::m_nDefaultWidth

指定應用程式中所有窗格分隔線的預設寬度 (以圖元為單位)。

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

##  <a name="move"></a>CPaneDivider:: Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>參數

[in] *ptOffset*<br/>
在*bAdjustLayout*<br/>

### <a name="remarks"></a>備註

##  <a name="m_psliderrtc"></a>CPaneDivider::m_pSliderRTC

保存有關`CPaneDivider`衍生物件的執行時間類別資訊的指標。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>備註

如果您建立自訂窗格分割線, 請設定這個成員變數。 這可讓架構在繪製窗格時建立窗格分割線。

### <a name="example"></a>範例

下列範例顯示如何設定`m_pSliderRTC`成員變數:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

##  <a name="notifyaboutrelease"></a>CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>備註

##  <a name="onshowpane"></a>CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>參數

在*pBar*<br/>
在*bShow*<br/>

### <a name="remarks"></a>備註

##  <a name="releaseemptypanecontainers"></a>CPaneDivider::ReleaseEmptyPaneContainers

```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>備註

##  <a name="removepane"></a>CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

在*pBar*<br/>

### <a name="remarks"></a>備註

##  <a name="replacepane"></a>CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>參數

[in] *pBarToReplace*<br/>
[in] *pBarToReplaceWith*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="repositionpanes"></a>CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>參數

[in] *rectNew*<br/>
[in] *hdwp*<br/>

### <a name="remarks"></a>備註

##  <a name="serialize"></a>CPaneDivider:: 序列化

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

[in] *ar*<br/>

### <a name="remarks"></a>備註

##  <a name="showwindow"></a>CPaneDivider:: ShowWindow

```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>參數

[in] *nCmdShow*<br/>

### <a name="remarks"></a>備註

##  <a name="storerecentdocksiteinfo"></a>CPaneDivider::StoreRecentDockSiteInfo

```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

在*pBar*<br/>

### <a name="remarks"></a>備註

##  <a name="storerecenttabrelatedinfo"></a>CPaneDivider::StoreRecentTabRelatedInfo

```
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>參數

[in] *pDockingBar*<br/>
在*pTabbedBar*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPaneContainerManager 類別](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane 類別](../../mfc/reference/cbasepane-class.md)
