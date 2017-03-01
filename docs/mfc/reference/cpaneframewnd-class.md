---
title: "CPaneFrameWnd 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneFrameWnd.Serialize
- CPaneFrameWnd.PreTranslateMessage
- CPaneFrameWnd
- CPaneFrameWnd::Serialize
- PreTranslateMessage
- CPaneFrameWnd::PreTranslateMessage
- Serialize
dev_langs:
- C++
helpviewer_keywords:
- CPaneFrameWnd class
- Serialize method
- PreTranslateMessage method
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8609643a9e64127af1d8035c496cedab4b1b1e9
ms.lasthandoff: 02/24/2017

---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd 類別
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 實作包含一個窗格的迷你框架視窗。 窗格會填滿視窗的工作區。  
  
## <a name="syntax"></a>語法  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPaneFrameWnd::AddPane](#addpane)|加入窗格。|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|從全域清單中加入或移除窗格。|  
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|調整迷你框架視窗的配置。|  
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||  
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|計算迷你框架視窗的框線大小。|  
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|計算預期的固定視窗矩形。|  
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|決定目前的窗格是否可以固定到另一個窗格或框架視窗。|  
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|決定迷你框架視窗是否可以固定到窗格。|  
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|將窗格轉換為索引標籤式文件。|  
|[CPaneFrameWnd::Create](#create)|建立迷你框架視窗，並將其附加至 `CPaneFrameWnd` 物件。|  
|[CPaneFrameWnd::CreateEx](#createex)|建立迷你框架視窗，並將其附加至 `CPaneFrameWnd` 物件。|  
|[CPaneFrameWnd::DockPane](#dockpane)|固定窗格。|  
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|在浮動窗格的全域清單中尋找具有指定控制項 ID 的窗格。|  
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|尋找包含使用者提供之點的迷你框架視窗。|  
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|傳回迷你框架視窗標題的高度。|  
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|傳回迷你框架視窗標題的週框。|  
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|傳回標題文字。|  
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||  
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|傳回固定模式。|  
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|傳回包含在迷你框架視窗中的第一個可見窗格。|  
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||  
|[CPaneFrameWnd::GetPane](#getpane)|傳回包含在迷你框架視窗中的窗格。|  
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|傳回包含在迷你框架視窗中的窗格數目。|  
|[CPaneFrameWnd::GetParent](#getparent)||  
|[CPaneFrameWnd::GetPinState](#getpinstate)||  
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||  
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|傳回包含在迷你框架視窗中的可見窗格數目。|  
|[CPaneFrameWnd::HitTest](#hittest)|判斷迷你框架視窗的哪個部分位於給定的點上。|  
|[CPaneFrameWnd::IsCaptured](#iscaptured)||  
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||  
|[CPaneFrameWnd::IsRollDown](#isrolldown)|決定是否應展開迷你框架視窗。|  
|[CPaneFrameWnd::IsRollUp](#isrollup)|決定是否應縮合迷你框架視窗。|  
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|停止固定計時器。|  
|[CPaneFrameWnd::LoadState](#loadstate)|從登錄載入窗格的狀態。|  
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|判斷是否可固定。|  
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|將迷你框架視窗固定在其最近的位置上。|  
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|停止彙總計時器。|  
|[CPaneFrameWnd::OnMovePane](#onmovepane)|以指定的位移移動迷你框架視窗。|  
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|調整所含窗格的配置。|  
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|設定彙總計時器。|  
|[CPaneFrameWnd::OnShowPane](#onshowpane)|在隱藏或顯示迷你框架視窗中的窗格時，由架構呼叫。|  
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|如果在迷你框架視窗內包含使用者提供的點，則會傳回一個窗格。|  
|[CPaneFrameWnd::Pin](#pin)||  
|`CPaneFrameWnd::PreTranslateMessage`|類別所使用的[CWinApp](../../mfc/reference/cwinapp-class.md)轉譯視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。|  
|[CPaneFrameWnd::RedrawAll](#redrawall)|重新繪製所有的迷你框架視窗。|  
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|由架構呼叫以移除無效窗格。|  
|[CPaneFrameWnd::RemovePane](#removepane)|從迷你框架視窗中移除窗格。|  
|[CPaneFrameWnd::ReplacePane](#replacepane)|以一個窗格取代另一個。|  
|[CPaneFrameWnd::SaveState](#savestate)|將窗格的狀態儲存至登錄。|  
|`CPaneFrameWnd::Serialize`|從封存中讀取或寫入此物件。|  
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|動作標題按鈕。|  
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||  
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||  
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|設定固定計時器。|  
|[CPaneFrameWnd::SetDockState](#setdockstate)|設定固定狀態。|  
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||  
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|由架構呼叫以設定預先固定狀態。|  
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|調整迷你框架視窗的大小，使其大小等同於所含窗格的大小。|  
|[CPaneFrameWnd::StartTearOff](#starttearoff)|清除功能表。|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|決定應縮合還是展開迷你框架視窗。|  
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|繪製迷你框架視窗的框線。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|指定是否要註冊具有 `CS_SAVEBITS` 類別樣式的視窗類別。|  
  
## <a name="remarks"></a>備註  
 當窗格從固定狀態切換至浮動狀態時，此架構會自動建立 `CPaneFrameWnd` 物件。  
  
 迷你框架視窗可在其內容可見的情況下進行拖曳 (即時固定)，或使用拖曳矩形 (標準固定)。 迷你框架容器窗格的固定模式會決定迷你框架的拖曳行為。 如需詳細資訊，請參閱[CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode)。  
  
 迷你框架視窗會根據包含的窗格樣式顯示標題的按鈕。 如果可以關閉窗格 ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed))，它會顯示 [關閉] 按鈕。 如果窗格具有 `AFX_CBRS_AUTO_ROLLUP` 樣式，則會顯示 pin。  
  
 如果您從 `CPaneFrameWnd` 衍生類別，您必須向架構指出如何建立該類別。 藉由覆寫建立類別[CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)，或設定`CPane::m_pMiniFrameRTC`成員，讓它指向您的類別的執行階段類別資訊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPaneFrameWnd`   
  
## <a name="requirements"></a>需求  
 **標頭︰** afxPaneFrameWnd.h  
  
##  <a name="a-nameaddpanea--cpaneframewndaddpane"></a><a name="addpane"></a>CPaneFrameWnd::AddPane  
 加入窗格。  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 若要新增窗格。  
  
##  <a name="a-nameaddremovepanefromgloballista--cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList  
 從全域清單中加入或移除窗格。  
  
```  
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,  
    BOOL bAdd);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 若要新增或移除窗格。  
  
 [in] `bAdd`  
 如果不是零，將窗格加入。 如果為 0，移除窗格。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
##  <a name="a-nameadjustlayouta--cpaneframewndadjustlayout"></a><a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout  
 調整迷你框架視窗的配置。  
  
```  
virtual void AdjustLayout();
```  
  
##  <a name="a-nameadjustpaneframesa--cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecalcbordersizea--cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize  
 計算自視窗框線的大小。  
  
```  
virtual void CalcBorderSize(CRect& rectBorderSize) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectBorderSize`  
 包含大小，單位為像素自視窗的框線。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構計算自視窗框線的大小。 傳回的大小取決於是否自視窗包含的工具列或[CDockablePane](../../mfc/reference/cdockablepane-class.md)。  
  
##  <a name="a-namecalcexpecteddockedrecta--cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect  
 計算預期的固定視窗矩形。  
  
```  
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndToDock`  
 若要停駐視窗的指標。  
  
 [in] `ptMouse`  
 滑鼠位置。  
  
 [輸出] `rectResult`  
 導出的矩形。  
  
 [輸出] `bDrawTab`  
 如果`TRUE`，繪製一個索引標籤。 如果`FALSE`，不繪製 索引標籤。  
  
 [輸出] `ppTargetBar`  
 [目標] 窗格的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會計算如果使用者拖曳到所指定的點的視窗，視窗會佔據的矩形`ptMouse`和那里其固定。  
  
##  <a name="a-namecanbeattacheda--cpaneframewndcanbeattached"></a><a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached  
 決定目前的窗格是否可以固定到另一個窗格或框架視窗。  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果另一個窗格或框架視窗，停駐窗格，否則`FALSE`。  
  
##  <a name="a-namecanbedockedtopanea--cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane  
 決定迷你框架視窗是否可以固定到窗格。  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockingBar`  
 一個窗格。  
  
### <a name="return-value"></a>傳回值  
 如果可以停駐迷你框架為非零`pDockingBar`，否則為 0。  
  
##  <a name="a-namecheckgrippervisibilitya--cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameconverttotabbeddocumenta--cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument  
 將窗格轉換為索引標籤式文件。  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
##  <a name="a-namecreatea--cpaneframewndcreate"></a><a name="create"></a>CPaneFrameWnd::Create  
 建立自視窗，並將它附加[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszWindowName`  
 指定要在自視窗中顯示的文字。  
  
 [in] `dwStyle`  
 指定的視窗樣式。 如需詳細資訊，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和自視窗的位置。  
  
 [in][out]`pParentWnd`  
 指定自視窗的父框架。 此值不能`NULL`。  
  
 [in][out]`pContext`  
 指定使用者定義的內容。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，建立視窗否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 自視窗會建立兩個步驟。 首先，架構就會建立`CPaneFrameWnd`物件。 第二，它會呼叫`Create`建立自視窗，並將其附加至`CPaneFrameWnd`物件。  
  
##  <a name="a-namecreateexa--cpaneframewndcreateex"></a><a name="createex"></a>CPaneFrameWnd::CreateEx  
 建立自視窗，並將它附加[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwStyleEx`  
 指定延伸的視窗樣式。 如需詳細資訊，請參閱[延伸視窗樣式](../../mfc/reference/extended-window-styles.md)  
  
 [in] `lpszWindowName`  
 指定要在自視窗中顯示的文字。  
  
 [in] `dwStyle`  
 指定的視窗樣式。 如需詳細資訊，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和自視窗的位置。  
  
 [in][out]`pParentWnd`  
 指定自視窗的父框架。 此值不能`NULL`。  
  
 [in][out]`pContext`  
 指定使用者定義的內容。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，建立視窗否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 自視窗會建立兩個步驟。 首先，架構就會建立`CPaneFrameWnd`物件。 第二，它會呼叫`Create`建立自視窗，並將其附加至`CPaneFrameWnd`物件。  
  
##  <a name="a-namedockpanea--cpaneframewnddockpane"></a><a name="dockpane"></a>CPaneFrameWnd::DockPane  
 固定窗格。  
  
```  
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `bWasDocked`  
 `TRUE`如果已固定窗格;，否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 如果作業成功，`CDockablePane`窗格已停駐，否則`NULL`。  
  
##  <a name="a-namefindfloatingpanebyida--cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID  
 在浮動窗格的全域清單中尋找具有指定控制項 ID 的窗格。  
  
```  
static CBasePane* FindFloatingPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 表示要尋找窗格的控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 窗格中，並指定的控制項 ID。否則， `NULL`，如果沒有窗格都有指定的控制項 id。  
  
##  <a name="a-nameframefrompointa--cpaneframewndframefrompoint"></a><a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint  
 尋找包含指定的點的迷你框架視窗。  
  
```  
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,  
    int nSensitivity,  
    CPaneFrameWnd* pFrameToExclude = NULL,  
    BOOL bFloatMultiOnly = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pt`  
 在螢幕座標的點。  
  
 [in] `nSensitivity`  
 增加此大小的迷你框架視窗的搜尋區域。 如果指定的點落在增加區域的迷你框架視窗可滿足搜尋條件。  
  
 [in] `pFrameToExclude`  
 指定要在搜尋中排除的迷你框架視窗。  
  
 [in] `bFloatMultiOnly`  
 如果`TRUE`，只搜尋迷你框架視窗`CBRS_FLOAT_MULTI`樣式。 如果`FALSE`，搜尋所有的迷你框架視窗。  
  
### <a name="return-value"></a>傳回值  
 包含的迷你框架視窗的指標`pt`，否則為`NULL`。  
  
##  <a name="a-namegetcaptionheighta--cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight  
 傳回迷你框架視窗標題的高度。  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素的迷你框架視窗。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來決定的迷你框架視窗的高度。 根據預設，高度設定為`SM_CYSMCAPTION`。 如需詳細資訊，請參閱[GetSystemMetrics 函式](http://msdn.microsoft.com/library/windows/desktop/ms724385)。  
  
##  <a name="a-namegetcaptionrecta--cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect  
 傳回迷你框架視窗標題的週框。  
  
```  
virtual void GetCaptionRect(CRect& rectCaption) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectCaption`  
 包含的大小和位置的迷你框架視窗標題、 在螢幕座標。  
  
### <a name="remarks"></a>備註  
 計算迷你框架視窗標題的周框矩形架構會呼叫這個方法。  
  
##  <a name="a-namegetcaptiontexta--cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText  
 傳回標題文字。  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>傳回值  
 迷你框架視窗的標題文字。  
  
### <a name="remarks"></a>備註  
 顯示的標題文字時，架構會呼叫這個方法。  
  
##  <a name="a-namegetdockingmanagera--cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetdockingmodea--cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode  
 傳回固定模式。  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 停駐的模式。 下列其中一個值：  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
##  <a name="a-namegetfirstvisiblepanea--cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane  
 傳回包含在迷你框架視窗中的第一個可見窗格。  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在迷你框架視窗中，第一個窗格或`NULL`如果迷你框架視窗會不包含任何窗格。  
  
##  <a name="a-namegethotpointa--cpaneframewndgethotpoint"></a><a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPoint GetHotPoint() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetpanea--cpaneframewndgetpane"></a><a name="getpane"></a>CPaneFrameWnd::GetPane  
 傳回包含在迷你框架視窗中的窗格。  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在迷你框架中包含的窗格或`NULL`如果迷你框架視窗會不包含任何窗格。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetpanecounta--cpaneframewndgetpanecount"></a><a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount  
 傳回包含在迷你框架視窗中的窗格數目。  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在迷你框架視窗的窗格數目。 這個值可以是零。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetparenta--cpaneframewndgetparent"></a><a name="getparent"></a>CPaneFrameWnd::GetParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CWnd* GetParent();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetpinstatea--cpaneframewndgetpinstate"></a><a name="getpinstate"></a>CPaneFrameWnd::GetPinState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetPinState() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetrecentfloatingrecta--cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetRecentFloatingRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetvisiblepanecounta--cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount  
 傳回包含在迷你框架視窗中的可見窗格數目。  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 顯示窗格數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehittesta--cpaneframewndhittest"></a><a name="hittest"></a>CPaneFrameWnd::HitTest  
 判斷迷你框架視窗的哪個部分位於給定的點上。  
  
```  
virtual LRESULT HitTest(
    CPoint point,  
    BOOL bDetectCaption);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 要測試的點。  
  
 [in] `bDetectCaption`  
 如果`TRUE`，檢查點針對標題。 如果`FALSE`，忽略標題。  
  
### <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
|值|意義|  
|-----------|-------------|  
|`HTNOWHERE`|重點是外部的迷你框架視窗。|  
|`HTCLIENT`|重點是工作區中。|  
|`HTCAPTION`|重點是標題。|  
|`HTTOP`|重點是在最上方。|  
|`HTTOPLEFT`|重點是在左上方。|  
|`HTTOPRIGHT`|重點是在右上方。|  
|`HTLEFT`|重點是在左側。|  
|`HTRIGHT`|重點是在右邊。|  
|`HTBOTTOM`|重點是底部。|  
|`HTBOTTOMLEFT`|重點是在左下方。|  
|`HTBOTTOMRIGHT`|重點是在右下方。|  
  
##  <a name="a-nameiscaptureda--cpaneframewndiscaptured"></a><a name="iscaptured"></a>CPaneFrameWnd::IsCaptured  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsCaptured() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdelayshowa--cpaneframewndisdelayshow"></a><a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDelayShow() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisrolldowna--cpaneframewndisrolldown"></a><a name="isrolldown"></a>CPaneFrameWnd::IsRollDown  
 決定是否應展開迷你框架視窗。  
  
```  
virtual BOOL IsRollDown() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果關閉; 必須復原迷你框架視窗否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構，以判斷是否應該關閉復原的迷你框架視窗。 如果它包含有至少一個窗格的迷你框架視窗啟用彙總套件/用功能`AFX_CBRS_AUTO_ROLLUP`旗標。 建立一個窗格時，會設定這個旗標。 如需詳細資訊，請參閱[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)。  
  
 根據預設，架構會檢查是否將滑鼠指標位於迷你框架視窗周框矩形，若要判斷視窗是否具有向下復原。 您可以覆寫衍生類別中的這個行為。  
  
##  <a name="a-nameisrollupa--cpaneframewndisrollup"></a><a name="isrollup"></a>CPaneFrameWnd::IsRollUp  
 決定是否應縮合迷你框架視窗。  
  
```  
virtual BOOL IsRollUp() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果迷你框架視窗必須彙總。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構判斷的迷你框架視窗是否將彙總。 如果它包含有至少一個窗格的迷你框架視窗啟用彙總套件/用功能`AFX_CBRS_AUTO_ROLLUP`旗標。 建立一個窗格時，會設定這個旗標。 如需詳細資訊，請參閱[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)。  
  
 根據預設，架構會檢查是否將滑鼠指標位於迷你框架視窗周框矩形，若要判斷視窗是否具有彙總。 您可以覆寫衍生類別中的這個行為。  
  
##  <a name="a-namekilldockingtimera--cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer  
 停止固定計時器。  
  
```  
void KillDockingTimer();
```  
  
##  <a name="a-nameloadstatea--cpaneframewndloadstate"></a><a name="loadstate"></a>CPaneFrameWnd::LoadState  
 從登錄載入窗格的狀態。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 設定檔名稱。  
  
 [in] `uiID`  
 窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 載入窗格狀態否則`FALSE`。  
  
##  <a name="a-namembusesavebitsa--cpaneframewndmbusesavebits"></a><a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits  
 指定是否要註冊視窗類別具有`CS_SAVEBITS`類別樣式。  
  
```  
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;  
```  
  
### <a name="remarks"></a>備註  
 這個靜態成員設定為`TRUE`登錄具有迷你框架視窗類別`CS_SAVEBITS`樣式。 這可能有助於減少當使用者拖曳的迷你框架視窗閃爍。  
  
##  <a name="a-nameonbeforedocka--cpaneframewndonbeforedock"></a><a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock  
 判斷是否可固定。  
  
```  
virtual BOOL OnBeforeDock();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可行，停駐否則， `FALSE`。  
  
##  <a name="a-nameoncheckrollstatea--cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState  
 決定應縮合還是展開迷你框架視窗。  
  
```  
virtual void OnCheckRollState();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構判斷向上或向下，是否應該復原的迷你框架視窗。  
  
 根據預設，架構會呼叫[CPaneFrameWnd::IsRollUp](#isrollup)和[CPaneFrameWnd::IsRollDown](#isrolldown)只是延伸或迷你框架視窗會還原。 您可以覆寫這個方法在衍生類別使用不同的視覺效果中。  
  
##  <a name="a-nameondocktorecentposa--cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos  
 將迷你框架視窗固定在其最近的位置上。  
  
```  
virtual void OnDockToRecentPos();
```  
  
##  <a name="a-nameondrawbordera--cpaneframewndondrawborder"></a><a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder  
 繪製迷你框架視窗的框線。  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容，用來繪製框線。  
  
### <a name="remarks"></a>備註  
 要繪製的迷你框架視窗框線架構會呼叫這個方法。  
  
##  <a name="a-nameonkillrolluptimera--cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer  
 停止彙總計時器。  
  
```  
virtual void OnKillRollUpTimer();
```  
  
##  <a name="a-nameonmovepanea--cpaneframewndonmovepane"></a><a name="onmovepane"></a>CPaneFrameWnd::OnMovePane  
 以指定的位移移動迷你框架視窗。  
  
```  
virtual void OnMovePane(
    CPane* pBar,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 （忽略） 窗格的指標。  
  
 [in] `ptOffset`  
 用來將窗格位移。  
  
##  <a name="a-nameonpanerecalclayouta--cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout  
 調整窗格的迷你框架視窗內的版面配置。  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>備註  
 它必須調整窗格的迷你框架視窗內的版面配置時，架構會呼叫這個方法。  
  
 根據預設，[] 窗格位於涵蓋完整的工作區的迷你框架視窗。  
  
##  <a name="a-nameonsetrolluptimera--cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer  
 設定彙總計時器。  
  
```  
virtual void OnSetRollUpTimer();
```  
  
##  <a name="a-nameonshowpanea--cpaneframewndonshowpane"></a><a name="onshowpane"></a>CPaneFrameWnd::OnShowPane  
 在隱藏或顯示迷你框架視窗中的窗格時，由架構呼叫。  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 正在窗格顯示或隱藏。  
  
 [in] `bShow`  
 `TRUE`如果正在顯示 窗格。`FALSE`如果隱藏窗格。  
  
### <a name="remarks"></a>備註  
 在迷你框架視窗中的窗格會顯示或隱藏時呼叫架構。 預設實作不做任何動作。  
  
##  <a name="a-namepina--cpaneframewndpin"></a><a name="pin"></a>CPaneFrameWnd::Pin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Pin(BOOL bPin = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPin`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namepanefrompointa--cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint  
 如果在迷你框架視窗內包含使用者提供的點，則會傳回一個窗格。  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 點螢幕座標中，使用者按一下。  
  
 [in] `nSensitivity`  
 不使用這個參數。  
  
 [in] `bCheckVisibility`  
 `TRUE`指定應該傳回只顯示的窗格。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 使用者按下，[] 窗格或`NULL`如果窗格不存在於該位置。  
  
### <a name="remarks"></a>備註  
 呼叫此方法來取得包含指定的點的窗格。  
  
##  <a name="a-nameredrawalla--cpaneframewndredrawall"></a><a name="redrawall"></a>CPaneFrameWnd::RedrawAll  
 重新繪製所有的迷你框架視窗。  
  
```  
static void RedrawAll();
```  
  
### <a name="remarks"></a>備註  
 這個方法會更新所有的迷你框架視窗呼叫[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)針對每個視窗。  
  
##  <a name="a-nameremovenonvalidpanesa--cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes  
 由架構呼叫以移除無效窗格。  
  
```  
virtual void RemoveNonValidPanes();
```  
  
##  <a name="a-nameremovepanea--cpaneframewndremovepane"></a><a name="removepane"></a>CPaneFrameWnd::RemovePane  
 從迷你框架視窗中移除窗格。  
  
```  
virtual void RemovePane(
    CBasePane* pWnd,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWnd`  
 若要移除窗格指標。  
  
 [in] `bDestroy`  
 指定的迷你框架視窗會發生什麼事。 如果`bDestroy`是`TRUE`，這個方法會立即終結迷你框架視窗。 如果是`FALSE`，這個方法會終結在特定的延遲之後的迷你框架視窗。  
  
 [in] `bNoDelayedDestroy`  
 如果`TRUE`、 延遲解構函式會停用。 如果`FALSE`、 延遲解構函式會啟用。  
  
### <a name="remarks"></a>備註  
 立即或在特定的延遲之後，架構可以終結迷你框架視窗。 如果您想要延遲的迷你框架視窗的解構函式，傳遞`FALSE`中`bNoDelayedDestroy`參數。 Framework 處理序時，就會發生延遲的解構`AFX_WM_CHECKEMPTYMINIFRAME`訊息。  
  
##  <a name="a-namereplacepanea--cpaneframewndreplacepane"></a><a name="replacepane"></a>CPaneFrameWnd::ReplacePane  
 以一個窗格取代另一個。  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBarOrg`  
 [原始] 窗格的指標。  
  
 [in] `pBarReplaceWith`  
 指標，會取代原始窗格的窗格。  
  
##  <a name="a-namesavestatea--cpaneframewndsavestate"></a><a name="savestate"></a>CPaneFrameWnd::SaveState  
 將窗格的狀態儲存至登錄。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 設定檔名稱。  
  
 [in] `uiID`  
 窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格狀態已經順利完成。否則`FALSE`。  
  
##  <a name="a-namesetcaptionbuttonsa--cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons  
 動作標題按鈕。  
  
```  
virtual void SetCaptionButtons(DWORD dwButtons);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwButtons`  
 下列值的位元 OR 組合︰  
  
- `AFX_CAPTION_BTN_CLOSE`  
  
- `AFX_CAPTION_BTN_PIN`  
  
- `AFX_CAPTION_BTN_MENU`  
  
- `AFX_CAPTION_BTN_CUSTOMIZE`  
  
##  <a name="a-namesetdelayshowa--cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetDelayShow(BOOL bDelayShow);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDelayShow`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetdockingmanagera--cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetDockingManager(CDockingManager* pManager);
```  
  
### <a name="parameters"></a>參數  
 [in] `pManager`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetdockingtimera--cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer  
 設定固定計時器。  
  
```  
void SetDockingTimer(UINT nTimeOut);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTimeOut`  
 逾時值以毫秒為單位。  
  
##  <a name="a-namesetdockstatea--cpaneframewndsetdockstate"></a><a name="setdockstate"></a>CPaneFrameWnd::SetDockState  
 設定固定狀態。  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockManager`  
 停駐 manager 指標。  
  
##  <a name="a-namesethotpointa--cpaneframewndsethotpoint"></a><a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetHotPoint(CPoint& ptNew);
```  
  
### <a name="parameters"></a>參數  
 [in] `ptNew`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetpredockstatea--cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState  
 由架構呼叫以設定預先固定狀態。  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `preDockState`  
 可能的值：  
  
- `PDS_NOTHING`,  
  
- `PDS_DOCK_REGULAR`,  
  
- `PDS_DOCK_TO_TAB`  
  
 [in] `pBarToDock`  
 若要停駐窗格的指標。  
  
 [in] `dockMethod`  
 停駐的方法。 （這個參數已忽略）。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果迷你框架視窗是卸除。`FALSE`如果停駐。  
  
##  <a name="a-namesizetocontenta--cpaneframewndsizetocontent"></a><a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent  
 調整的迷你框架視窗的大小，使它相當於所包含的窗格。  
  
```  
virtual void SizeToContent();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以調整大小的迷你框架視窗包含窗格的大小。  
  
##  <a name="a-namestarttearoffa--cpaneframewndstarttearoff"></a><a name="starttearoff"></a>CPaneFrameWnd::StartTearOff  
 清除功能表。  
  
```  
BOOL StartTearOff(CMFCPopu* pMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMenu`  
 功能表指標。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功則為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="a-namestorerecentdocksiteinfoa--cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namestorerecenttabrelatedinfoa--cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockingBar`  
 [in] `pTabbedBar`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)

