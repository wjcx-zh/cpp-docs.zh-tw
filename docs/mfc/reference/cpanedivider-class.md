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
ms.openlocfilehash: 0ebac4e18f65d789d5196266d57184744ad5ad28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753624"
---
# <a name="cpanedivider-class"></a>CPaneDivider 類別

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

類`CPaneDivider`劃分兩個窗格,劃分兩組窗格,或從主框架視窗的工作區分隔一組窗格。

## <a name="syntax"></a>語法

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPaneDivider:CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPaneDivider::添加窗格容器](#addpanecontainer)||
|[CPaneDivider::添加窗格](#addpane)||
|[CPaneDivider::添加最新窗格](#addrecentpane)||
|[CPaneDivider::卡爾西德多克雷茨](#calcexpecteddockedrect)||
|[CPaneDivider::鈣固定佈局](#calcfixedlayout)|(覆蓋[CBasePane::CalcFixed 佈局](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::檢查可見性](#checkvisibility)||
|[CPaneDivider::創建Ex](#createex)|(覆蓋[CBasePane:createEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::D允許在之前插入](#doesallowdyninsertbefore)|(覆蓋[CBasePane::DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CPaneDivider::D包含浮動窗格](#doescontainfloatingpane)||
|[CPaneDivider::查找窗格容器](#findpanecontainer)||
|[CPaneDivider::尋找標籤窗格](#findtabbedpane)||
|[CPaneDivider:取得預設寬度](#getdefaultwidth)||
|[CPaneDivider:取得第一窗格](#getfirstpane)||
|[CPaneDivider::取得窗格分線器樣式](#getpanedividerstyle)||
|[CPaneDivider::獲取根容器重新完成](#getrootcontainerrect)||
|[CPaneDivider:獲取寬度](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::插入窗格](#insertpane)||
|[CPaneDivider::是自動隱藏模式](#isautohidemode)|( 覆[寫 CBasePane:是自動隱藏模式](../../mfc/reference/cbasepane-class.md#isautohidemode)。|
|[CPaneDivider:預設](#isdefault)||
|[CPaneDivider:是水準的](#ishorizontal)|(覆蓋[CBasePane:是水準](../../mfc/reference/cbasepane-class.md#ishorizontal)的 。)|
|[CPaneDivider::移動](#move)||
|[CPaneDivider::通知發佈](#notifyaboutrelease)||
|[CPaneDivider::在顯示窗格上](#onshowpane)||
|[CPaneDivider::釋放空窗格容器](#releaseemptypanecontainers)||
|[CPaneDivider::刪除窗格](#removepane)||
|[CPaneDivider::替換窗格](#replacepane)||
|[CPaneDivider::重新置放窗格](#repositionpanes)||
|[CPaneDivider:序列化](#serialize)|(覆寫 `CBasePane::Serialize`。)|
|[CPaneDivider::設定自動隱藏模式](#setautohidemode)||
|[CPaneDivider::設定窗格容器管理員](#setpanecontainermanager)||
|[CPaneDivider::顯示視窗](#showwindow)||
|[CPaneDivider::存儲最新網站資訊](#storerecentdocksiteinfo)||
|[CPaneDivider::存儲最新標籤相關信息](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPaneDivider::獲取窗格](#getpanes)|返回駐留在[CPane 容器類](../../mfc/reference/cpanecontainer-class.md)中的窗格的清單。 此方法應僅針對預設窗格分隔符調用。|
|[CPaneDivider::取得窗格分頻器](#getpanedividers)|返回駐留在[CPane 容器類](../../mfc/reference/cpanecontainer-class.md)中的窗格分隔符的清單。 此方法應僅針對預設窗格分隔符調用。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CPaneDivider:m_nDefaultWidth](#m_ndefaultwidth)|指定應用程式中所有窗格分隔符的預設寬度(以像素為單位)。|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|保存指向有關派生物件的運行時類資訊的`CPaneDivider`指標。|

## <a name="remarks"></a>備註

當窗格停靠`CPaneDivider`時,框架會自動創建物件。

有兩種類型的窗格分隔符:

- 當一組窗格停靠在主框架視窗的一側時,將創建預設窗格分隔符。 默認窗格分隔符包含指向[CPaneContainerManager 類](../../mfc/reference/cpanecontainermanager-class.md)的指標,並將窗格組上的大多數操作(例如調整窗格大小或停靠另一個窗格或容器)重定向到容器管理器。 每個停靠窗格都維護指向其預設窗格分隔符的指標。

- 常規窗格分隔符只需在容器中劃分兩個窗格。 有關詳細資訊,請參閱[CPane 容器類](../../mfc/reference/cpanecontainer-class.md)。

## <a name="example"></a>範例

下列範例示範如何從 `CWorkspaceBar` 物件取得 `CPaneDivider` 物件。 此代碼段是[MDI 選項卡演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目標](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>需求

**標題:** afxPaneDivider.h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a>CPaneDivider::設定自動隱藏模式

```cpp
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>參數

[在]*bMode*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a>CPaneDivider::設定窗格容器管理員

```cpp
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>參數

[在]*p*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedivideraddpane"></a><a name="addpane"></a>CPaneDivider::添加窗格

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a>CPaneDivider::添加窗格容器

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

[在]*酒吧容器管理員*<br/>
[在]*bouterEdge*<br/>
[在]*p 目標列*<br/>
[在]*dwalignment*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a>CPaneDivider::添加最新窗格

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneDivider::卡爾西德多克雷茨

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>參數

[在]*普恩德托多克*<br/>
[在]*ptMouse*<br/>
[在]*rectResult*<br/>
[在]*bDrawTab*<br/>
[在]*ppTargetBar*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a>CPaneDivider::鈣固定佈局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[在]*b 伸*<br/>
[在]*布霍茲*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a>CPaneDivider::檢查可見性

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a>CPaneDivider:CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>參數

[在]*b預設滑動*<br/>
[在]*p 父級*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividercreateex"></a><a name="createex"></a>CPaneDivider::創建Ex

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

[在]*dwStyleEx*<br/>
[在]*dwStyle*<br/>
[在]*rect*<br/>
[在]*pparentwnd*<br/>
[在]*nID*<br/>
[在]*pContext*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CPaneDivider::D允許在之前插入

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a>CPaneDivider::D包含浮動窗格

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a>CPaneDivider::查找窗格容器

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>
[在]*b左欄*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a>CPaneDivider::尋找標籤窗格

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>參數

[在]*nID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a>CPaneDivider:取得預設寬度

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a>CPaneDivider:取得第一窗格

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a>CPaneDivider::取得窗格分頻器

返回駐留在[CPane 容器類](../../mfc/reference/cpanecontainer-class.md)中的窗格分隔符的清單。 此方法應僅針對預設窗格分隔符調用。

```cpp
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>參數

*lstSliders*<br/>
[出]包含駐留在窗格容器中的窗格分隔符的清單。

### <a name="remarks"></a>備註

此方法應僅針對預設窗格分隔符調用。 預設窗格分隔符是調整整個窗格容器大小的分隔符。

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a>CPaneDivider::取得窗格分線器樣式

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a>CPaneDivider::獲取窗格

返回駐留在[CPane 容器類](../../mfc/reference/cpanecontainer-class.md)中的窗格的清單。 應僅調用此方法來檢索預設窗格分隔符。

```cpp
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>參數

*lstBars*<br/>
[出]包含駐留在窗格容器中的窗格的清單。

### <a name="remarks"></a>備註

此方法應僅針對預設窗格分隔符調用。 預設窗格分隔符是調整整個窗格容器大小的分隔符。

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a>CPaneDivider::獲取根容器重新完成

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a>CPaneDivider:獲取寬度

```
int GetWidth() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerinit"></a><a name="init"></a>CPaneDivider::Init

```cpp
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>參數

[在]*b預設滑動*<br/>
[在]*p 父級*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a>CPaneDivider::插入窗格

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>參數

[在]*pBarto 插入*<br/>
[在]*p 目標列*<br/>
[在]*dwalignment*<br/>
[在]*lpRect*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a>CPaneDivider::是自動隱藏模式

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a>CPaneDivider:預設

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a>CPaneDivider:是水準的

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a>CPaneDivider:m_nDefaultWidth

指定應用程式中所有窗格分隔符的預設寬度(以像素為單位)。

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a>CPaneDivider::移動

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>參數

[在]*pt 位移*<br/>
[在]*b 調整佈局*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a>CPaneDivider::m_pSliderRTC

保存指向有關派生物件的運行時類資訊的`CPaneDivider`指標。

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>備註

如果創建自定義窗格分隔符,請設置此成員變數。 這使框架能夠在繪製窗格時創建窗格分隔符。

### <a name="example"></a>範例

下面的範例展示如何設定`m_pSliderRTC`成員變數:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a>CPaneDivider::通知發佈

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>備註

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a>CPaneDivider::在顯示窗格上

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>
[在]*b 顯示*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CPaneDivider::釋放空窗格容器

```cpp
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>備註

## <a name="cpanedividerremovepane"></a><a name="removepane"></a>CPaneDivider::刪除窗格

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a>CPaneDivider::替換窗格

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>參數

[在]*pBarto 取代*<br/>
[在]*pbarto 取代為*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a>CPaneDivider::重新置放窗格

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>參數

[在]*重新*<br/>
[在]*hdwp*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerserialize"></a><a name="serialize"></a>CPaneDivider:序列化

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

[在]*阿爾*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a>CPaneDivider::顯示視窗

```cpp
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>參數

[在]*nCmdShow*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneDivider::存儲最新網站資訊

```cpp
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>參數

[在]*pBar*<br/>

### <a name="remarks"></a>備註

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneDivider::存儲最新標籤相關信息

```cpp
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>參數

[在]*pDockingBar*<br/>
[在]*pTabbedBar*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPaneContainerManager 類別](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer 類別](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager 類別](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane 類別](../../mfc/reference/cbasepane-class.md)
