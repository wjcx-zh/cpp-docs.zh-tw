---
title: "CPane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPane
dev_langs:
- C++
helpviewer_keywords:
- CPane class
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: 30
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 586133277aa4a9d89ca15cdd496a1ca7e4232632
ms.lasthandoff: 02/24/2017

---
# <a name="cpane-class"></a>CPane Class
`CPane`類別是一項增強功能的[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)。 如果您要升級現有的 MFC 專案，取代所有出現的`CControlBar`與`CPane`。  
  
## <a name="syntax"></a>語法  
  
```  
class CPane : public CBasePane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CPane::~CPane`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|立刻重新計算 窗格的版面配置。|  
|[CPane::AllocElements](#allocelements)|配置儲存區供內部使用。|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|指定是否列於執行階段產生的清單中的應用程式 窗格的窗格。|  
|[CPane::CalcAvailableSize](#calcavailablesize)|計算的大小指定的矩形和目前的視窗矩形之間的差異。|  
|[CPane::CalcInsideRect](#calcinsiderect)|計算內部矩形之框線和夾納入考量的窗格。|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|會計算最近停駐的矩形。|  
|[CPane::CalcSize](#calcsize)|計算窗格的大小。|  
|[CPane::CanBeDocked](#canbedocked)|判斷是否可以在指定的基底窗格停駐窗格。|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|判斷是否窗格可以轉換成索引標籤式文件。|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|將索引標籤式文件中的可停駐窗格。|  
|[CPane::CopyState](#copystate)|將複製之窗格的狀態。 (覆寫[CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate)。)|  
|[CPane::Create](#create)|建立一種控制列，並將它附加`CPane`物件。|  
|[CPane::CreateDefaultMiniframe](#createdefaultminiframe)|建立浮動窗格的迷你框架視窗。|  
|[CPane::CreateEx](#createex)|建立一種控制列，並將它附加`CPane`物件。|  
|`CPane::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CPane::DockByMouse](#dockbymouse)|使用滑鼠停駐方法停駐窗格。|  
|[CPane::DockPane](#dockpane)|浮動窗格停駐於基底的窗格。|  
|[CPane::DockPaneStandard](#dockpanestandard)|使用大綱 （標準） 的停駐停駐窗格。|  
|[CPane::DockToFrameWindow](#docktoframewindow)|可停駐窗格停駐於框架。 (覆寫 `CBasePane::DockToFrameWindow`。)|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|指出是否可以停駐在相同的資料列會在停駐 [目前] 窗格中的另一個窗格。|  
|[CPane::FloatPane](#floatpane)|浮動窗格。|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|傳回量，單位為像素，可以展開窗格。|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|傳回量，單位為像素，可以縮小窗格。|  
|[CPane::GetBorders](#getborders)|傳回窗格的框線寬度。|  
|[CPane::GetClientHotSpot](#getclienthotspot)|傳回*作用點*窗格。|  
|[CPane::GetDockSiteRow](#getdocksiterow)|傳回的窗格即停駐的停駐列。|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|判斷是否在資料列獨佔模式中窗格。|  
|[CPane::GetHotSpot](#gethotspot)|傳回儲存在基準的作用`CMFCDragFrameImpl`物件。|  
|[CPane::GetMinSize](#getminsize)|擷取的最小允許大小的窗格。|  
|[CPane::GetPaneName](#getpanename)|擷取窗格的標題。|  
|`CPane::GetResizeStep`|在內部使用。|  
|`CPane::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CPane::GetVirtualRect](#getvirtualrect)|擷取*虛擬矩形*的窗格。|  
|[CPane::IsChangeState](#ischangestate)|移動 [] 窗格時，這個方法會分析相對於其他窗格、 停駐列迷你框架視窗窗格的位置，並傳回適當`AFX_CS_STATUS`值。|  
|[CPane::IsDragMode](#isdragmode)|指定是否要拖曳窗格。|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定是否在多窗格框架視窗窗格。 (覆寫 `CBasePane::IsInFloatingMultiPaneFrameWnd`。)|  
|[CPane::IsLeftOf](#isleftof)|決定是否窗格 （或以上） 保留指定的矩形。|  
|[CPane::IsResizable](#isresizable)|判斷是否可以調整窗格的大小。 (覆寫[CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable)。)|  
|[CPane::IsTabbed](#istabbed)|判斷是否已插入的索引標籤式視窗索引標籤控制項 窗格。 (覆寫[CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed)。)|  
|[CPane::LoadState](#loadstate)|從登錄載入窗格的狀態。 (覆寫[CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate)。)|  
|[CPane::MoveByAlignment](#movebyalignment)|根據指定的數量會移動窗格及虛擬的矩形。|  
|[CPane::MovePane](#movepane)|將窗格移至指定的矩形。|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|架構變更窗格的父代時呼叫。|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|架構 [] 窗格中的父代變更時呼叫。|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|在使用者選擇的標題 窗格的 關閉 按鈕時，由架構呼叫。|  
|`CPane::OnProcessDblClk`|在內部使用。|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|當特殊窗格功能表即將顯示時由架構呼叫。|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|當特殊窗格功能表即將顯示時由架構呼叫。|  
|`CPane::PrepareToDock`|在內部使用。|  
|[CPane::RecalcLayout](#recalclayout)|重新計算配置資訊窗格。 (覆寫[CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout)。)|  
|[CPane::SaveState](#savestate)|將窗格的狀態儲存至登錄。 (覆寫[CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate)。)|  
|[CPane::SetActiveInGroup](#setactiveingroup)|旗標設為作用中 窗格。|  
|[CPane::SetBorders](#setborders)|設定框線的值 窗格。|  
|[CPane::SetClientHotSpot](#setclienthotspot)|設定作用點的窗格。|  
|[CPane::SetDockState](#setdockstate)|還原停駐窗格的狀態資訊。|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|啟用或停用獨佔資料列模式。|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|設定預設的迷你框架視窗的執行階段類別資訊。|  
|[CPane::SetMinSize](#setminsize)|設定允許窗格大小的最小。|  
|[CPane::SetVirtualRect](#setvirtualrect)|設定*虛擬矩形*的窗格。|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|延伸垂直或水平根據停駐樣式 窗格。|  
|[CPane::ToggleAutoHide](#toggleautohide)|切換自動隱藏模式。|  
|[CPane::UndockPane](#undockpane)|移除停駐位置、 預設滑桿或目前固定的迷你框架視窗的窗格。 (覆寫[CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane)。)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|更新虛擬矩形。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|已停駐窗格時，由架構呼叫。|  
|[CPane::OnAfterFloat](#onafterfloat)|浮動窗格時，由架構呼叫。|  
|[CPane::OnBeforeDock](#onbeforedock)|停駐窗格時，由架構呼叫。|  
|[CPane::OnBeforeFloat](#onbeforefloat)|浮動窗格時，由架構呼叫。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|可讓一致的處理方式窗格的最小大小。|  
|[CPane::m_recentDockInfo](#m_recentdockinfo)|包含新的停駐資訊。|  
  
## <a name="remarks"></a>備註  
 一般而言，`CPane`物件無法直接執行個體化。 如果您需要有功能停駐窗格時，衍生您的物件從[CDockablePane](../../mfc/reference/cdockablepane-class.md)。 如果您需要工具列功能時，衍生您的物件從[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)。  
  
 當您衍生自`CPane`，可以在停駐[CDockSite](../../mfc/reference/cdocksite-class.md)和浮動在[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxPane.h  
  
##  <a name="a-nameadjustsizeimmediatea--cpaneadjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CPane::AdjustSizeImmediate  
 立刻重新計算 窗格的版面配置。  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bRecalcLayout`  
 `TRUE`若要自動重新計算配置的窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當您以動態方式變更窗格的版面配置時，請呼叫這個方法。 比方說，您可能想要隱藏或顯示工具列按鈕時呼叫這個方法。  
  
##  <a name="a-nameallocelementsa--cpaneallocelements"></a><a name="allocelements"></a>CPane::AllocElements  
 配置儲存區供內部使用。  
  
```  
BOOL AllocElements(
    int nElements,  
    int cbElement);
```  
  
### <a name="parameters"></a>參數  
 [in] `nElements`  
 這是要將存放裝置配置的項目數目。  
  
 [in] `cbElement`  
 大小 （位元組） 項目。  
  
### <a name="return-value"></a>傳回值  
 `FALSE`如果記憶體配置失敗。否則， `TRUE`。  
  
##  <a name="a-nameallowshowonpanemenua--cpaneallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CPane::AllowShowOnPaneMenu  
 指定是否列於執行階段產生的清單中的應用程式 窗格的窗格。  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格會顯示在清單中。否則， `FALSE`。 基底實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 AppWizard 產生的應用程式包含它所包含的窗格會列出的功能表選項。 這個方法會決定是否在清單中顯示 窗格。  
  
##  <a name="a-namecalcavailablesizea--cpanecalcavailablesize"></a><a name="calcavailablesize"></a>CPane::CalcAvailableSize  
 計算的大小指定的矩形和目前的視窗矩形之間的差異。  
  
```  
virtual CSize CalcAvailableSize(CRect rectRequired);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectRequired`  
 必要的矩形。  
  
### <a name="return-value"></a>傳回值  
 寬度和高度之間的差異`rectRequired`和目前視窗的矩形。  
  
##  <a name="a-namecalcinsiderecta--cpanecalcinsiderect"></a><a name="calcinsiderect"></a>CPane::CalcInsideRect  
 計算內部的窗格中，包括框線和夾的矩形。  
  
```  
void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rect`  
 包含大小和工作區 窗格的位移。  
  
 [in] `bHorz`  
 `TRUE`如果窗格是水平空間。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 必須重新計算配置給窗格時，架構會呼叫這個方法。 `rect`填入參數的大小和工作區 窗格的位移。 這包括其框線和夾。  
  
##  <a name="a-namecalcrecentdockedrecta--cpanecalcrecentdockedrect"></a><a name="calcrecentdockedrect"></a>CPane::CalcRecentDockedRect  
 會計算最近停駐的矩形。  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>備註  
 這個方法會更新[CPane::m_recentDockInfo](#m_recentdockinfo)。  
  
##  <a name="a-namecalcsizea--cpanecalcsize"></a><a name="calcsize"></a>CPane::CalcSize  
 計算窗格的大小。  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>參數  
 [in] `bVertDock`  
 `TRUE`如果以垂直方式，停駐窗格`FALSE`否則。  
  
### <a name="return-value"></a>傳回值  
 這個方法的預設實作會傳回大小為 （0，0）。  
  
### <a name="remarks"></a>備註  
 在衍生的類別應該覆寫這個方法。  
  
##  <a name="a-namecanbedockeda--cpanecanbedocked"></a><a name="canbedocked"></a>CPane::CanBeDocked  
 決定是否可在指定的基底窗格停駐窗格。  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockBar`  
 指定此窗格為停駐窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此窗格可停駐在指定的停駐窗格。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法通常稱為架構，以判斷是否可以在指定的停駐窗格停駐窗格。 若要判斷方法是否可以停駐窗格中，目前計算結果窗格的啟用停駐的對齊方式。  
  
 您可以啟用各種側邊的框架視窗停駐，藉由呼叫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="a-namecanbetabbeddocumenta--cpanecanbetabbeddocument"></a><a name="canbetabbeddocument"></a>CPane::CanBeTabbedDocument  
 決定是否窗格可以轉換成索引標籤式文件。  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格可以轉換為索引標籤式文件。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，並傳回`FALSE`如果您想要防止被轉換為索引標籤式文件 窗格。 索引標籤式文件將不會列在視窗的位置 功能表中。  
  
##  <a name="a-nameconverttotabbeddocumenta--cpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPane::ConvertToTabbedDocument  
 將索引標籤式文件中的可停駐窗格。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActiveTabOnly`  
 中不使用`CPane::ConvertToTabbedDocument`。  
  
### <a name="remarks"></a>備註  
 只可停駐窗格可以轉換成索引標籤式文件中。 如需資訊，請參閱[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。  
  
##  <a name="a-namecopystatea--cpanecopystate"></a><a name="copystate"></a>CPane::CopyState  
 將複製之窗格的狀態。  
  
```  
virtual void CopyState(CPane* pOrgBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pOrgBar`  
 窗格的指標。  
  
### <a name="remarks"></a>備註  
 這個方法會複製狀態的`pOrgBar`到目前的窗格。  
  
##  <a name="a-namecreatea--cpanecreate"></a><a name="create"></a>CPane::Create  
 建立一種控制列，並將它附加[CPane](../../mfc/reference/cpane-class.md)物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszClassName`  
 指定的視窗類別名稱。  
  
 [in] `dwStyle`  
 指定的視窗樣式屬性。 如需詳細資訊，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和位置`pParentWnd` 視窗中的，在工作區座標。  
  
 [in][out]`pParentWnd`  
 指定此窗格中的父視窗。  
  
 [in] `nID`  
 指定窗格的識別碼。  
  
 [in] `dwControlBarStyle`  
 指定的樣式 窗格。 如需詳細資訊，請參閱[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)。  
  
 [in][out]`pContext`  
 指定建立的內容窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 建立窗格否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法建立視窗窗格，並將它附加`CPane`物件。  
  
 如果您未明確初始化[CPane::m_recentDockInfo](#m_recentdockinfo)之前先呼叫`Create`，參數`rect`用作矩形時浮動或停駐窗格。  
  
##  <a name="a-namecreatedefaultminiframea--cpanecreatedefaultminiframe"></a><a name="createdefaultminiframe"></a>CPane::CreateDefaultMiniframe  
 建立浮動窗格的迷你框架視窗。  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectInitial`  
 指定的初始大小和位置，在螢幕座標中的迷你框架視窗建立。  
  
### <a name="return-value"></a>傳回值  
 新建立的迷你框架視窗。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構建立浮動窗格的迷你框架視窗。 迷你框架視窗可以是類型[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)或型別的[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)。 如果窗格都有，則會建立多迷你框架視窗`AFX_CBRS_FLOAT_MULTI`樣式。  
  
 迷你框架視窗的執行階段類別資訊會儲存在`CPane::m_pMiniFrameRTC`成員。 您可以使用衍生的類別，將這個成員的設定，如果您決定要建立自訂的迷你框架視窗。  
  
##  <a name="a-namecreateexa--cpanecreateex"></a><a name="createex"></a>CPane::CreateEx  
 建立一種控制列，並將它附加[CPane](../../mfc/reference/cpane-class.md)物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwStyleEx`  
 指定延伸的視窗樣式屬性。 如需詳細資訊，請參閱[延伸視窗樣式](../../mfc/reference/extended-window-styles.md)。  
  
 [in] `lpszClassName`  
 指定的視窗類別名稱。  
  
 [in] `dwStyle`  
 指定視窗的樣式屬性。 如需詳細資訊，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `rect`  
 指定的初始大小和位置`pParentWnd` 視窗中的，在工作區座標。  
  
 [in][out]`pParentWnd`  
 指定此窗格中的父視窗。  
  
 [in] `nID`  
 指定窗格的識別碼。  
  
 [in] `dwControlBarStyle`  
 指定的樣式 窗格。 如需詳細資訊，請參閱[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)。  
  
 [in][out]`pContext`  
 指定建立內容窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 建立窗格否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法建立視窗窗格，並將它附加`CPane`物件。  
  
 如果您未明確初始化[CPane::m_recentDockInfo](#m_recentdockinfo)之前先呼叫`CreateEx`，參數`rect`用作矩形時浮動或停駐窗格。  
  
##  <a name="a-namedockbymousea--cpanedockbymouse"></a><a name="dockbymouse"></a>CPane::DockByMouse  
 使用滑鼠停駐窗格。  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockBar`  
 指定要停駐此窗格的基底的窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 停駐窗格，否則， `FALSE`。  
  
##  <a name="a-namedockpanea--cpanedockpane"></a><a name="dockpane"></a>CPane::DockPane  
 浮動窗格停駐於基底的窗格。  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pDockBar`  
 指定基底的窗格，即可停駐這個窗格。  
  
 [in] `lpRect`  
 在基底所在停駐此窗格的窗格中指定的矩形。  
  
 [in] `dockMethod`  
 指定要使用的停駐的方法。 可用的選項如下所示︰  
  
|選項|說明|  
|------------|-----------------|  
|`DM_UNKNOWN`|未知的停駐的方法時，架構會使用此選項。 窗格不會儲存其最新位置。 您也可以使用此選項時沒有儲存新位置，以程式設計的方式停駐窗格。|  
|`DM_MOUSE`|在內部使用。|  
|`DM_DBL_CLICK`|移駐夾按兩下時，會使用此選項。 窗格會在其最新的停駐位置重新定位。 如果按兩下浮動窗格的窗格中已重新定位在其最新位置。|  
|`DM_SHOW`|此選項可用來以程式設計的方式停駐窗格。 窗格會儲存其最新位置。|  
|`DM_RECT`|所指定之區域中停駐窗格`lpRect`。|  
|`DM_STANDARD`|當您使用此選項時，架構窗格當做繪製外框框架正在移動時。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 停駐窗格，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法窗格停駐於所指定的基底窗格`pDockBar`參數。 您必須先啟用停駐藉由呼叫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="a-namedockpanestandarda--cpanedockpanestandard"></a><a name="dockpanestandard"></a>CPane::DockPaneStandard  
 使用大綱 （標準） 的停駐停駐窗格。  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>參數  
 [in] `bWasDocked`  
 `TRUE`如果已成功固定窗格;，否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 此方法一律傳回`this`指標。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於衍生自的窗格[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)。 如需詳細資訊，請參閱[CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard)。  
  
##  <a name="a-namedocktoframewindowa--cpanedocktoframewindow"></a><a name="docktoframewindow"></a>CPane::DockToFrameWindow  
 可停駐窗格停駐於框架。  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 您想要停駐窗格的父框架端。  
  
 [in] `lpRect`  
 指定的大小。  
  
 [in] `dwDockFlags`  
 忽略。  
  
 [in] `pRelativeBar`  
 忽略。  
  
 [in] `nRelativeIndex`  
 忽略。  
  
 [in] `bOuterEdge`  
 如果`TRUE`而且沒有其他可停駐窗格旁邊所指定的`dwAlignment`，窗格即停駐以外其他窗格，接近的父框架邊緣。 如果`FALSE`，窗格停駐在接近用戶端區域的中央。  
  
### <a name="return-value"></a>傳回值  
 `FALSE`如果窗格分割線 ( [CPaneDivider 類別](../../mfc/reference/cpanedivider-class.md)) 建立，否則不能是`TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedoesallowsiblingbarsa--cpanedoesallowsiblingbars"></a><a name="doesallowsiblingbars"></a>CPane::DoesAllowSiblingBars  
 指出是否可以停駐在相同的資料列會在停駐 [目前] 窗格中的另一個窗格。  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果這個窗格可以到另一個窗格停駐在相同的資料列本身;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以啟用或停用此行為，藉由呼叫[CPane::SetExclusiveRowMode](#setexclusiverowmode)。  
  
 根據預設，工具列已停用的資料列獨佔模式和功能表列中已啟用的資料列獨佔模式。  
  
##  <a name="a-namefloatpanea--cpanefloatpane"></a><a name="floatpane"></a>CPane::FloatPane  
 浮動窗格。  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod = DM_UNKNOWN,  
    bool bShow = true);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectFloat`  
 當它浮動定位窗格的螢幕座標中指定的位置。  
  
 [in] `dockMethod`  
 指定的停駐方法窗格浮動時使用。 如需可能的值，請參閱[CPane::DockPane](#dockpane)。  
  
 [in] `bShow`  
 `TRUE`若要顯示窗格時浮動。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功浮動窗格，或無法浮動窗格，因為[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)傳回`FALSE`，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以浮動窗格中所指定的位置`rectFloat`參數。 這個方法會自動建立父迷你框架視窗窗格。  
  
##  <a name="a-namegetavailableexpandsizea--cpanegetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CPane::GetAvailableExpandSize  
 傳回量，單位為像素，可以展開窗格。  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果水平停駐窗格中，則傳回值是可用的寬度。否則，傳回的值會是可用的高度。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetavailablestretchsizea--cpanegetavailablestretchsize"></a><a name="getavailablestretchsize"></a>CPane::GetAvailableStretchSize  
 傳回量，單位為像素，可以縮小窗格。  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 像素為單位，可以縮小窗格的數量。 水平停駐窗格中，如果此數量不包括可用的寬度。否則，它是可用的高度。  
  
### <a name="remarks"></a>備註  
 可用的自動縮放大小的計算方式減去允許窗格大小的最小 ( [CPane::GetMinSize](#getminsize)) 從目前的大小 ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect))。  
  
##  <a name="a-namegetbordersa--cpanegetborders"></a><a name="getborders"></a>CPane::GetBorders  
 傳回窗格的框線寬度。  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) ，其中包含目前的寬度，單位為像素的窗格中的每一端的物件。 例如，值`left`成員`CRect`物件是左框線的寬度。  
  
### <a name="remarks"></a>備註  
 若要設定框線的大小，請呼叫[CPane::SetBorders](#setborders)。  
  
##  <a name="a-namegetclienthotspota--cpanegetclienthotspot"></a><a name="getclienthotspot"></a>CPane::GetClientHotSpot  
 傳回*作用點*窗格。  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 *作用點*是在窗格中，使用者會選取並移動窗格保存點。 作用點可用於動畫更為順暢，窗格從停駐位置移動時。  
  
##  <a name="a-namegetdocksiterowa--cpanegetdocksiterow"></a><a name="getdocksiterow"></a>CPane::GetDockSiteRow  
 傳回固定資料列 ( [CDockingPanesRow 類別](../../mfc/reference/cdockingpanesrow-class.md)) 中的窗格即停駐。  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A `CDockingPanesRow`*，以指到停駐窗格中的停駐列或`NULL`如果未停駐窗格。  
  
##  <a name="a-namegetexclusiverowmodea--cpanegetexclusiverowmode"></a><a name="getexclusiverowmode"></a>CPane::GetExclusiveRowMode  
 決定窗格是獨佔的資料列模式。  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格是獨佔資料列模式，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如需獨佔資料列模式的詳細資訊，請參閱[CPane::SetExclusiveRowMode](#setexclusiverowmode)。  
  
##  <a name="a-namegethotspota--cpanegethotspot"></a><a name="gethotspot"></a>CPane::GetHotSpot  
 傳回儲存在基準的作用`CMFCDragFrameImpl`物件。  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 `CPane`類別包含`CMFCDragFrameImpl`物件， `m_dragFrameImpl`，也就是負責繪製使用者以標準停駐模式移動窗格時出現的矩形。 作用點用來繪製矩形相對於目前的滑鼠位置，當使用者移動的窗格。  
  
##  <a name="a-namegetminsizea--cpanegetminsize"></a><a name="getminsize"></a>CPane::GetMinSize  
 擷取的最小允許大小的窗格。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `size`  
 A`CSize`填滿允許大小的最小的物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetpanenamea--cpanegetpanename"></a><a name="getpanename"></a>CPane::GetPaneName  
 擷取窗格的標題。  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strName`  
 A`CString`填滿的標題名稱的物件。  
  
### <a name="remarks"></a>備註  
 停駐或浮動窗格時，窗格的標題會顯示在標題區域中。 如果窗格是索引標籤式群組的一部分，標題會顯示索引標籤區域中。 如果窗格自動隱藏模式中，標題會顯示在`CMFCAutoHideButton`。  
  
##  <a name="a-namegetvirtualrecta--cpanegetvirtualrect"></a><a name="getvirtualrect"></a>CPane::GetVirtualRect  
 擷取*虛擬矩形*的窗格。  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectVirtual`  
 A`CRect`虛擬矩形填滿的物件。  
  
### <a name="remarks"></a>備註  
 當移動窗格時，架構會儲存到原始位置 窗格的虛擬矩形中。 架構可用來還原到原始位置 窗格的虛擬矩形。  
  
 不要呼叫方法，除非您要以程式設計的方式移動窗格與虛擬的矩形。  
  
##  <a name="a-nameischangestatea--cpaneischangestate"></a><a name="ischangestate"></a>CPane::IsChangeState  
 移動 [] 窗格時，這個方法會分析它的位置，相對於其他窗格、 停駐列迷你框架視窗，並傳回適當`AFX_CS_STATUS`值。  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `nOffset`  
 指定停駐的敏感度。 例如，內移動窗格`nOffset`像素為單位，從停駐的資料列將會停駐。  
  
 [in] `ppTargetBar`  
 方法傳回時，`ppTargetBar`包含物件的目前窗格應該停駐，指標或`NULL`停駐不應該發生。  
  
### <a name="return-value"></a>傳回值  
 下列其中一種`AFX_CS_STATUS`值︰  
  
|值|說明|  
|-----------|-----------------|  
|`CS_NOTHING`|[] 窗格並未停駐位置附近。 架構不會不停駐窗格。|  
|`CS_DOCK_IMMEDIATELY`|是透過停駐位置，而`DT_IMMEDIATE`樣式已啟用。 架構立即停駐窗格。|  
|`CS_DELAY_DOCK`|是透過與另一個停駐窗格或主要畫面格的邊緣的停駐位置。 當使用者放開滑鼠移動架構停駐窗格。|  
|`CS_DELAY_DOCK_TO_TAB`|是透過停駐在索引標籤式視窗中，窗格會停駐位置。 會發生這種情況是當窗格可以透過另一個停駐窗格的標題，或在索引標籤式窗格的索引標籤區域。 當使用者放開滑鼠移動架構停駐窗格。|  
  
##  <a name="a-nameisdragmodea--cpaneisdragmode"></a><a name="isdragmode"></a>CPane::IsDragMode  
 指定是否正在移動的窗格。  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果正在移動的窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisinfloatingmultipaneframewnda--cpaneisinfloatingmultipaneframewnd"></a><a name="isinfloatingmultipaneframewnd"></a>CPane::IsInFloatingMultiPaneFrameWnd  
 指定是否在多窗格框架視窗窗格 ( [CMultiPaneFrameWnd 類別](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格中的多窗格框架視窗。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 多窗格在框架視窗中浮動只可停駐窗格。 因此，`CPane::IsInFloatingMultiPaneFrameWnd`一律會傳回`FALSE`。  
  
##  <a name="a-nameisleftofa--cpaneisleftof"></a><a name="isleftof"></a>CPane::IsLeftOf  
 決定是否窗格 （或以上） 保留指定的矩形。  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 A`CRect`用於比較的物件。  
  
 [in] `bWindowRect`  
 如果`TRUE`，`rect`假設為包含螢幕座標中; 如果`FALSE`，`rect`假設為包含用戶端座標。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如果水平停駐窗格中，這個方法會檢查它的位置，是否要保留的`rect`。 否則，這個方法會檢查位置是否之上`rect`。  
  
##  <a name="a-nameisresizablea--cpaneisresizable"></a><a name="isresizable"></a>CPane::IsResizable  
 指定是否可調整大小的窗格。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果是可調整大小;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 基底`CPane`物件不是可調整大小。  
  
 停駐的管理員會使用可調整大小的旗標，來決定窗格版面配置。 非可調整大小的窗格是永遠位於父框架外緣。  
  
 非可調整大小的窗格不能位於停駐容器。  
  
##  <a name="a-nameistabbeda--cpaneistabbed"></a><a name="istabbed"></a>CPane::IsTabbed  
 決定窗格是否已插入至索引標籤式視窗的索引標籤控制項。  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤式窗格。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 索引標籤式的狀態從浮點分開處理，停駐，而自動隱藏狀態。  
  
##  <a name="a-nameloadstatea--cpaneloadstate"></a><a name="loadstate"></a>CPane::LoadState  
 從登錄載入窗格的狀態。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 設定檔名稱。  
  
 [in] `nIndex`  
 設定檔的索引。  
  
 [in] `uiID`  
 窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 載入窗格狀態否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以從登錄載入窗格狀態。 儲存所載入的其他資訊的衍生類別中覆寫它[CPane::SaveState](#savestate)。  
  
 當您覆寫這個方法時，也呼叫基底方法，並傳回`FALSE`如果基底方法會傳回`FALSE`。  
  
##  <a name="a-namembhandleminsizea--cpanembhandleminsize"></a><a name="m_bhandleminsize"></a>CPane::m_bHandleMinSize  
 可讓一致的處理方式最小值 窗格的大小。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>備註  
 如果您的應用程式中的一個或多個停駐窗格覆寫`GetMinSize`，或是如果您的應用程式呼叫`SetMinSize`，您可能要將這個靜態成員設定`TRUE`若要讓架構一致的方式處理窗格大小的方式。  
  
 如果此值設為`TRUE`，裁剪所有窗格的大小，因此可減少低於其最小的大小，不會自動縮放。 由於架構使用基於窗格調整大小的視窗區域，不會變更的視窗區域，如果此值設為停駐窗格的大小`TRUE`。  
  
##  <a name="a-namemrecentdockinfoa--cpanemrecentdockinfo"></a><a name="m_recentdockinfo"></a>CPane::m_recentDockInfo  
 包含新的停駐資訊。  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>備註  
 架構會在這個成員中儲存的最新的停駐窗格的狀態資訊。  
  
##  <a name="a-namemovebyalignmenta--cpanemovebyalignment"></a><a name="movebyalignment"></a>CPane::MoveByAlignment  
 根據指定的數量會移動窗格及虛擬的矩形。  
  
```  
BOOL MoveByAlignment(
    DWORD dwAlignment,  
    int nOffset);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
 指定窗格對齊方式。  
  
 [in] `nOffset`  
 要移動的窗格和虛擬矩形的像素為單位數量。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 `dwAlignment`可以是下列值之一︰  
  
|值|說明|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|可讓可停駐於框架視窗的工作區頂端的窗格。|  
|`CBRS_ALIGN_BOTTOM`|可讓工作區框架視窗的底部停駐窗格。|  
|`CBRS_ALIGN_LEFT`|可讓可停駐於框架視窗的工作區左邊的窗格。|  
|`CBRS_ALIGN_RIGHT`|可讓可停駐於框架視窗的工作區右下方的窗格。|  
|`CBRS_ALIGN_ANY`|可讓任何一側，框架視窗的工作區的固定窗格。|  
  
 如果`dwAlignment`包含`CBRS_ALIGN_LEFT`或`CBRS_ALIGN_RIGHT`旗標、 窗格和虛擬矩形會水平; 否則如果移動`dwAlignment`包含`CBRS_ALIGN_TOP`或`CBRS_ALIGN_BOTTOM`旗標、 窗格和虛擬的矩形垂直移動。  
  
##  <a name="a-namemovepanea--cpanemovepane"></a><a name="movepane"></a>CPane::MovePane  
 將窗格移至指定的矩形。  
  
```  
virtual CSize MovePane(
    CRect rectNew,  
    BOOL bForceMove,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectNew`  
 指定新的矩形的窗格。  
  
 [in] `bForceMove`  
 如果`TRUE`，這個方法會略過的最小允許的窗格大小 ( [CPane::GetMinSize](#getminsize)); 否則，請調整 [] 窗格中，如有必要，以確保它至少是允許的大小最小值。  
  
 [in] `hdwp`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含新的和舊的矩形之間的寬度和高度差異 (舊的矩形 – `rectNew`)。  
  
### <a name="remarks"></a>備註  
 這個方法只適用於可停駐窗格。  
  
##  <a name="a-nameonafterchangeparenta--cpaneonafterchangeparent"></a><a name="onafterchangeparent"></a>CPane::OnAfterChangeParent  
 架構變更窗格的父代時呼叫。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pWndOldParent`  
 前一個父視窗的窗格。  
  
### <a name="remarks"></a>備註  
 停駐或浮動作業變更窗格的父代時，架構會呼叫這個方法。  
  
##  <a name="a-nameonafterdocka--cpaneonafterdock"></a><a name="onafterdock"></a>CPane::OnAfterDock  
 已停駐窗格時，由架構呼叫。  
  
```  
virtual void OnAfterDock(
    CBasePane* pBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 不使用這個參數。  
  
 [in] `lpRect`  
 不使用這個參數。  
  
 [in] `dockMethod`  
 不使用這個參數。  
  
##  <a name="a-nameonafterfloata--cpaneonafterfloat"></a><a name="onafterfloat"></a>CPane::OnAfterFloat  
 浮動窗格之後，由架構呼叫。  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>備註  
 如果您想要執行任何處理之後會浮動在窗格中，您可以覆寫這個方法在衍生類別中。  
  
##  <a name="a-nameonbeforechangeparenta--cpaneonbeforechangeparent"></a><a name="onbeforechangeparent"></a>CPane::OnBeforeChangeParent  
 架構 [] 窗格中的父代變更時呼叫。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pWndNewParent`  
 指定新的父視窗。  
  
 [in] `bDelay`  
 `TRUE`若要延遲全域的停駐配置調整。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 因為窗格正在變更窗格的父代時，呼叫這個方法由架構停駐或浮動。  
  
 根據預設，[] 窗格中的註冊停駐窗格與藉由呼叫`CDockSite::RemovePane`。  
  
##  <a name="a-nameonbeforedocka--cpaneonbeforedock"></a><a name="onbeforedock"></a>CPane::OnBeforeDock  
 若要停駐窗格時，由架構呼叫。  
  
```  
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`ppDockBar`  
 指定此窗格停駐窗格。  
  
 [in] `lpRect`  
 指定的停駐的矩形。  
  
 [in] `dockMethod`  
 指定的停駐的方法。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可停駐窗格。 如果此函數會傳回`FALSE`，停駐的作業將會中止。  
  
### <a name="remarks"></a>備註  
 停駐窗格時，架構會呼叫這個方法。 如果您想要執行任何處理，最後會停駐窗格之前，您可以覆寫這個方法在衍生類別中。  
  
##  <a name="a-nameonbeforefloata--cpaneonbeforefloat"></a><a name="onbeforefloat"></a>CPane::OnBeforeFloat  
 窗格即將浮點數時，由架構呼叫。  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectFloat`  
 處於浮動狀態時，指定的位置和大小的窗格。  
  
 [in] `dockMethod`  
 指定停駐窗格的方法。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以浮動窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 窗格即將浮點數時，架構會呼叫這個方法。 如果您想要執行任何處理，最後浮動窗格之前，您可以覆寫這個方法在衍生類別中。  
  
##  <a name="a-nameonpressclosebuttona--cpaneonpressclosebutton"></a><a name="onpressclosebutton"></a>CPane::OnPressCloseButton  
 在窗格的標題，使用者按下 [關閉] 按鈕時呼叫架構。  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>備註  
 當使用者按下時，呼叫這個方法由架構**關閉**窗格的標題上的按鈕。 若要接收通知的相關**關閉**事件，您可以覆寫這個方法在衍生類別中的。  
  
##  <a name="a-nameonshowcontrolbarmenua--cpaneonshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CPane::OnShowControlBarMenu  
 當特殊窗格功能表即將顯示時由架構呼叫。  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指定功能表位置。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以顯示功能表。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 該功能表包含數個項目可讓您指定窗格的行為，也就是︰**浮動**，**停駐**，**自動隱藏**，和**隱藏**。 您可以藉由呼叫啟用所有窗格這個功能表[CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu)。  
  
##  <a name="a-namerecalclayouta--cpanerecalclayout"></a><a name="recalclayout"></a>CPane::RecalcLayout  
 重新計算配置資訊窗格。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
 如果窗格即停駐，這個方法會更新窗格的虛擬矩形大小設為 [] 窗格中的目前大小。  
  
 如果浮動窗格，這個方法會通知父迷你框架來調整窗格的迷你框架大小的大小。 此架構可確保迷你框架至少是允許窗格大小的最小 ( [CPane::GetMinSize](#getminsize)) 並視需要調整迷你框架的大小。  
  
##  <a name="a-namesavestatea--cpanesavestate"></a><a name="savestate"></a>CPane::SaveState  
 將窗格的狀態儲存至登錄。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 設定檔名稱。  
  
 [in] `nIndex`  
 設定檔的索引。  
  
 [in] `uiID`  
 窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果儲存的狀態已順利啟動。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 窗格的狀態儲存至登錄時，架構會呼叫這個方法。 覆寫`SaveState`儲存其他資訊在衍生類別中。  
  
 當您覆寫這個方法時，也呼叫基底方法，並傳回`FALSE`如果基底方法會傳回`FALSE`。  
  
##  <a name="a-namesetactiveingroupa--cpanesetactiveingroup"></a><a name="setactiveingroup"></a>CPane::SetActiveInGroup  
 旗標設為作用中 窗格。  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActive`  
 A `BOOL` ，指定是否標示為作用中 窗格。  
  
### <a name="remarks"></a>備註  
 會顯示可停駐窗格或選擇 [自動隱藏] 按鈕時，對應的自動隱藏窗格會標記為作用中。  
  
 窗格與相關聯的自動隱藏 按鈕的外觀根據兩個因素而定。 如果窗格為作用中，而`static``BOOL``CMFCAutoHideButton::m_bOverlappingTabs`是`TRUE`，架構會顯示為圖示和標籤的 [自動隱藏] 按鈕。 為非作用中 窗格中，架構會顯示自動隱藏圖示。  
  
 如果`CMFCAutoHideButton::m_bOverlappingTabs`是`FALSE`，或如果窗格不在群組中，架構會顯示相關聯的自動隱藏 按鈕圖示和標籤。  
  
##  <a name="a-namesetbordersa--cpanesetborders"></a><a name="setborders"></a>CPane::SetBorders  
 設定框線的值 窗格。  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 [in] `cxLeft`  
 指定寬度，單位為像素窗格的左框線。  
  
 [in] `cyTop`  
 指定寬度，單位為像素窗格的上框線。  
  
 [in] `cxRight`  
 指定寬度，單位為像素窗格的右框線。  
  
 [in] `cyBottom`  
 指定寬度，單位為像素的窗格下框線。  
  
 [in] `lpRect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含的寬度，以像素為單位，每個窗格的框線。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可設定的窗格框線的大小。  
  
##  <a name="a-namesetclienthotspota--cpanesetclienthotspot"></a><a name="setclienthotspot"></a>CPane::SetClientHotSpot  
 設定*作用點*窗格。  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>參數  
 [in] `ptNew`  
 A`CPoint`物件，指定新的作用點。  
  
### <a name="remarks"></a>備註  
 *作用點*是在窗格中，使用者會選取並移動窗格保存點。 作用點可用於動畫更為順暢，從停駐位置拖曳窗格時。  
  
##  <a name="a-namesetdockstatea--cpanesetdockstate"></a><a name="setdockstate"></a>CPane::SetDockState  
 還原停駐窗格的狀態資訊。  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDockManager`  
 主框架視窗的連接管理員的指標。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法是由架構還原最近停駐窗格的狀態資訊。 窗格會儲存最新的停駐狀態資訊在[CPane::m_recentDockInfo](#m_recentdockinfo)。 如需詳細資訊，請參閱[CRecentDockSiteInfo 類別](../../mfc/reference/crecentdocksiteinfo-class.md)。  
  
 您也可以呼叫這個方法，當您從外部來源載入窗格資訊設定的銜接狀態。  
  
##  <a name="a-namesetexclusiverowmodea--cpanesetexclusiverowmode"></a><a name="setexclusiverowmode"></a>CPane::SetExclusiveRowMode  
 啟用或停用獨佔資料列模式。  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bExclusive`  
 `TRUE`若要啟用獨佔資料列模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來啟用或停用獨佔資料列模式。 資料列獨佔模式窗格時，它無法共用相同的資料列的其他工具列。  
  
 根據預設，所有的工具列已停用的資料列獨佔模式和功能表列中已啟用的資料列獨佔模式。  
  
##  <a name="a-namesetminsizea--cpanesetminsize"></a><a name="setminsize"></a>CPane::SetMinSize  
 設定允許窗格大小的最小。  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>參數  
 [in] `size`  
 A`CSize`物件，其中包含允許窗格大小的最小。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetvirtualrecta--cpanesetvirtualrect"></a><a name="setvirtualrect"></a>CPane::SetVirtualRect  
 設定*虛擬矩形*的窗格。  
  
```  
void SetVirtualRect(
    const CRect& rect,  
    BOOL bMapToParent = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
 A`CRect`物件，指定要設定的虛擬矩形。  
  
 [in] `bMapToParent`  
 指定`TRUE`如果`rect`包含相對於父視窗的點。  
  
### <a name="remarks"></a>備註  
 A*虛擬矩形*移動時，儲存到原始位置 窗格。 架構可以使用的虛擬矩形還原到原始位置。  
  
 不要呼叫方法，除非您要以程式設計的方式移動窗格與虛擬的矩形。  
  
##  <a name="a-namesetminiframertca--cpanesetminiframertc"></a><a name="setminiframertc"></a>CPane::SetMiniFrameRTC  
 設定預設的迷你框架視窗的執行階段類別資訊。  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pClass`  
 指定的迷你框架視窗的執行階段類別資訊。  
  
### <a name="remarks"></a>備註  
 當浮動窗格時，放[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) （迷你框架） 視窗。 您可以提供自訂`CPaneFrameWnd`-衍生類別，將會使用的時機[CPane::CreateDefaultMiniframe](#createdefaultminiframe)稱為。  
  
##  <a name="a-namestretchpanedeferwndposa--cpanestretchpanedeferwndpos"></a><a name="stretchpanedeferwndpos"></a>CPane::StretchPaneDeferWndPos  
 延伸垂直或水平根據停駐樣式 窗格。  
  
```  
virtual int StretchPaneDeferWndPos(
    int nStretchSize,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>參數  
 [in] `nStretchSize`  
 像素為單位，以延伸窗格數量。 您可以使用負數值來壓縮 窗格。  
  
 [in] `hdwp`  
 未使用。  
  
### <a name="return-value"></a>傳回值  
 實際的量，單位為像素已伸展的窗格。  
  
### <a name="remarks"></a>備註  
 如果有必要，這個方法會修改`nStretchSize`以確保窗格不會超過大小限制。 這些限制由呼叫[CPane::GetAvailableStretchSize](#getavailablestretchsize)和[CPane::GetAvailableExpandSize](#getavailableexpandsize)。  
  
##  <a name="a-nametoggleautohidea--cpanetoggleautohide"></a><a name="toggleautohide"></a>CPane::ToggleAutoHide  
 切換自動隱藏模式。  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以切換自動隱藏模式。 窗格必須切換到 自動隱藏模式，才能停駐到主框架視窗之用。  
  
##  <a name="a-nameundockpanea--cpaneundockpane"></a><a name="undockpane"></a>CPane::UndockPane  
 移除停駐位置、 預設滑桿或目前固定的迷你框架視窗的窗格。  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDelay`  
 如果`FALSE`，架構會呼叫[CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)調整停駐配置。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法，以程式設計方式取消停駐窗格。  
  
##  <a name="a-nameupdatevirtualrecta--cpaneupdatevirtualrect"></a><a name="updatevirtualrect"></a>CPane::UpdateVirtualRect  
 更新虛擬矩形。  
  
```  
void UpdateVirtualRect();  
void UpdateVirtualRect(CPoint ptOffset);  
  void UpdateVirtualRect(CSize sizeNew);
```  
  
### <a name="parameters"></a>參數  
 [in] `ptOffset`  
 A`CPoint`物件，指定用來移位窗格中的位移。  
  
 [in] `sizeNew`  
 A`CSize`物件，指定 [] 窗格中的新大小。  
  
### <a name="remarks"></a>備註  
 第一個多載會使用目前的位置和窗格的大小，設定虛擬矩形。  
  
 第二個多載移位量所指定的虛擬矩形`ptOffset`。  
  
 第三個多載使用窗格和所指定的大小目前的位置，設定的虛擬矩形`sizeNew`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBasePane 類別](../../mfc/reference/cbasepane-class.md)

