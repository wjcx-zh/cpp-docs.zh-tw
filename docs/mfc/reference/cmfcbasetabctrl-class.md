---
title: "CMFCBaseTabCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseTabCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseTabCtrl class
ms.assetid: 7270c55f-6f6e-4dd2-b0d2-291afeac3882
caps.latest.revision: 41
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
ms.openlocfilehash: d82cde70595bf6d7a4629f54cc48e2b422cd5e8c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasetabctrl-class"></a>CMFCBaseTabCtrl 類別
實作索引標籤式視窗的基本功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCBaseTabCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::AddIcon](#addicon)||  
|[CMFCBaseTabCtrl::AddTab](#addtab)|將新的索引標籤加入至索引標籤式視窗。|  
|[CMFCBaseTabCtrl::ApplyRestoredTabInfo](#applyrestoredtabinfo)||  
|[CMFCBaseTabCtrl::AutoDestroyWindow](#autodestroywindow)||  
|[CMFCBaseTabCtrl::CalcRectEdit](#calcrectedit)||  
|[CMFCBaseTabCtrl::CleanUp](#cleanup)||  
|[CMFCBaseTabCtrl::ClearImageList](#clearimagelist)||  
|[CMFCBaseTabCtrl::DetachTab](#detachtab)|從索引標籤式視窗中斷連結索引標籤。|  
|[CMFCBaseTabCtrl::EnableActivateLastActive](#enableactivatelastactive)||  
|[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)|啟用或停用自動索引標籤著色。|  
|[CMFCBaseTabCtrl::EnableCustomToolTips](#enablecustomtooltips)|啟用或停用索引標籤的自訂工具提示。|  
|[CMFCBaseTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|啟用或停用索引標籤的直接編輯。|  
|[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)|啟用可中斷連結的索引標籤。|  
|[CMFCBaseTabCtrl::EnableTabSwap](#enabletabswap)|啟用或停用使用者是否可以利用滑鼠變更索引標籤順序。|  
|[CMFCBaseTabCtrl::EnsureVisible](#ensurevisible)|將索引標籤捲動直到看見指定的索引標籤。 如果指定的索引標籤已經可見，則表示這個方法沒有任何作用。|  
|[CMFCBaseTabCtrl::EnterDragMode](#enterdragmode)||  
|[CMFCBaseTabCtrl::FindTargetWnd](#findtargetwnd)|傳回包含指定點的窗格。|  
|[CMFCBaseTabCtrl::FireChangeActiveTab](#firechangeactivetab)||  
|[CMFCBaseTabCtrl::FireChangingActiveTab](#firechangingactivetab)||  
|[CMFCBaseTabCtrl::GetActiveTab](#getactivetab)|傳回使用中索引標籤的索引。|  
|[CMFCBaseTabCtrl::GetActiveTabColor](#getactivetabcolor)|傳回使用中索引標籤的背景色彩。|  
|[CMFCBaseTabCtrl::GetActiveTabTextColor](#getactivetabtextcolor)|傳回使用中索引標籤的文字色彩。|  
|[CMFCBaseTabCtrl::GetActiveWnd](#getactivewnd)|傳回索引標籤控制項之使用中頁面的指標。|  
|[CMFCBaseTabCtrl::GetAutoColors](#getautocolors)|傳回用於自動上色之色彩陣列的參考。|  
|[CMFCBaseTabCtrl::GetFirstVisibleTab](#getfirstvisibletab)|傳回第一個可見索引標籤的指標。|  
|[CMFCBaseTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)||  
|[CMFCBaseTabCtrl::GetHighlightedTab](#gethighlightedtab)|傳回目前反白顯示之索引標籤的索引。|  
|[CMFCBaseTabCtrl::GetImageList](#getimagelist)||  
|[CMFCBaseTabCtrl::GetImageSize](#getimagesize)||  
|[CMFCBaseTabCtrl::GetLastVisibleTab](#getlastvisibletab)||  
|[CMFCBaseTabCtrl::GetLocation](#getlocation)|傳回 LOCATION 資料類型的變數，指出索引標籤區域相對於索引標籤控制項的位置。 例如，在頂端或底部。|  
|[CMFCBaseTabCtrl::GetMaxWindowSize](#getmaxwindowsize)||  
|[CMFCBaseTabCtrl::GetTabArea](#gettabarea)|傳回索引標籤式視窗中索引標籤區域的大小和位置。 使用座標定義索引標籤區域的位置。|  
|[CMFCBaseTabCtrl::GetTabBkColor](#gettabbkcolor)|傳回指定之索引標籤的背景色彩。|  
|[CMFCBaseTabCtrl::GetTabBorderSize](#gettabbordersize)|傳回索引標籤控制項中索引標籤框線的大小。|  
|[CMFCBaseTabCtrl::GetTabByID](#gettabbyid)|傳回指定之識別碼所識別的索引標籤索引|  
|[CMFCBaseTabCtrl::GetTabCloseButton](#gettabclosebutton)||  
|[CMFCBaseTabCtrl::GetTabFromHwnd](#gettabfromhwnd)|傳回包含指定之 HWND 物件的索引標籤索引。|  
|[CMFCBaseTabCtrl::GetTabFromPoint](#gettabfrompoint)|傳回包含指定點的索引標籤。|  
|[CMFCBaseTabCtrl::GetTabFullWidth](#gettabfullwidth)||  
|[CMFCBaseTabCtrl::GetTabHicon](#gettabhicon)|傳回與指定之索引標籤相關聯的圖示。|  
|[CMFCBaseTabCtrl::GetTabID](#gettabid)|使用索引標籤的索引，傳回索引標籤的識別碼。|  
|[CMFCBaseTabCtrl::GetTabIcon](#gettabicon)|傳回指定之索引標籤的圖示識別碼。|  
|[CMFCBaseTabCtrl::GetTabLabel](#gettablabel)|傳回指定之索引標籤的文字。|  
|[CMFCBaseTabCtrl::GetTabRect](#gettabrect)|擷取指定之索引標籤的大小與位置。|  
|[CMFCBaseTabCtrl::GetTabsHeight](#gettabsheight)||  
|[CMFCBaseTabCtrl::GetTabsRect](#gettabsrect)||  
|[CMFCBaseTabCtrl::GetTabTextColor](#gettabtextcolor)|傳回指定之索引標籤的文字色彩。|  
|[CMFCBaseTabCtrl::GetTabWnd](#gettabwnd)|傳回位於指定的索引標籤頁面之窗格的指標。|  
|[CMFCBaseTabCtrl::GetTabWndNoWrapper](#gettabwndnowrapper)|傳回位於指定的索引標籤之控制項的直接指標，即使控制項有包裝函式也一樣。|  
|[CMFCBaseTabCtrl::GetTabsNum](#gettabsnum)|傳回索引標籤控制項中包含的索引標籤數目。|  
|[CMFCBaseTabCtrl::GetToolTipCtrl](#gettooltipctrl)|傳回與 `CMFCBaseTabCtrl` 物件相關聯之工具提示控制項的參照。|  
|[CMFCBaseTabCtrl::GetVisibleTabsNum](#getvisibletabsnum)|傳回可見索引標籤的數目。|  
|[CMFCBaseTabCtrl::HasImage](#hasimage)||  
|[CMFCBaseTabCtrl::HideSingleTab](#hidesingletab)|設定隱藏視窗索引標籤的選項，但前提是索引標籤式視窗只顯示一個可見的索引標籤。|  
|[CMFCBaseTabCtrl::InsertTab](#inserttab)|插入新的索引標籤。|  
|[CMFCBaseTabCtrl::InvalidateTab](#invalidatetab)||  
|[CMFCBaseTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)||  
|[CMFCBaseTabCtrl::IsAutoColor](#isautocolor)|傳回值，指出索引標籤式視窗是否處於自動色彩模式。|  
|[CMFCBaseTabCtrl::IsAutoDestroyWindow](#isautodestroywindow)||  
|[CMFCBaseTabCtrl::IsColored](#iscolored)||  
|[CMFCBaseTabCtrl::IsDialogControl](#isdialogcontrol)||  
|[CMFCBaseTabCtrl::IsDrawNoPrefix](#isdrawnoprefix)||  
|[CMFCBaseTabCtrl::IsFlatFrame](#isflatframe)|傳回值，指出索引標籤區域的框架是平面或 3D。|  
|[CMFCBaseTabCtrl::IsFlatTab](#isflattab)||  
|[CMFCBaseTabCtrl::IsHideSingleTab](#ishidesingletab)|傳回值，指出索引標籤控制項是否設定為隱藏索引標籤，但前提是索引標籤式視窗只有一個可見的索引標籤。|  
|[CMFCBaseTabCtrl::IsIconAdded](#isiconadded)||  
|[CMFCBaseTabCtrl::IsInPlaceEdit](#isinplaceedit)|指出使用者是否可以修改索引標籤上的標籤。|  
|[CMFCBaseTabCtrl::IsLeftRightRounded](#isleftrightrounded)||  
|[CMFCBaseTabCtrl::IsMDITab](#ismditab)||  
|[CMFCBaseTabCtrl::IsOneNoteStyle](#isonenotestyle)|指出索引標籤式視窗是否以 Microsoft OneNote 樣式顯示索引標籤。|  
|[CMFCBaseTabCtrl::IsPtInTabArea](#isptintabarea)|檢查索引標籤區域中是否存在指定的點。|  
|[CMFCBaseTabCtrl::IsTabCloseButtonHighlighted](#istabclosebuttonhighlighted)||  
|[CMFCBaseTabCtrl::IsTabCloseButtonPressed](#istabclosebuttonpressed)||  
|[CMFCBaseTabCtrl::IsTabDetachable](#istabdetachable)|指出是否可以中斷連結索引標籤。|  
|[CMFCBaseTabCtrl::IsTabIconOnly](#istabicononly)|指出索引標籤是否顯示圖示，但不顯示標籤。|  
|[CMFCBaseTabCtrl::IsTabSwapEnabled](#istabswapenabled)|指出使用者是否可以拖曳索引標籤來變更索引標籤位置。|  
|[CMFCBaseTabCtrl::IsTabVisible](#istabvisible)|指出指定的索引標籤是否可見。|  
|[CMFCBaseTabCtrl::IsVS2005Style](#isvs2005style)||  
|[CMFCBaseTabCtrl::MoveTab](#movetab)||  
|[CMFCBaseTabCtrl::OnChangeTabs](#onchangetabs)|索引標籤數目變更時由架構呼叫。|  
|[CMFCBaseTabCtrl::OnDragEnter](#ondragenter)||  
|[CMFCBaseTabCtrl::OnDragLeave](#ondragleave)||  
|[CMFCBaseTabCtrl::OnDragOver](#ondragover)||  
|[CMFCBaseTabCtrl::OnDrop](#ondrop)||  
|[CMFCBaseTabCtrl::OnRenameTab](#onrenametab)||  
|[CMFCBaseTabCtrl::PreTranslateMessage](#pretranslatemessage)|類別所使用的[CWinApp](../../mfc/reference/cwinapp-class.md)轉譯視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCBaseTabCtrl::RecalcLayout](#recalclayout)|重新計算索引標籤式視窗的內部配置。|  
|[CMFCBaseTabCtrl::RemoveAllTabs](#removealltabs)|從索引標籤式視窗中移除所有索引標籤。|  
|[CMFCBaseTabCtrl::RemoveTab](#removetab)|從索引標籤式視窗中移除一個索引標籤。|  
|[CMFCBaseTabCtrl::RenameTab](#renametab)||  
|[CMFCBaseTabCtrl::ResetImageList](#resetimagelist)|重設附加至索引標籤式視窗的映像清單。|  
|[CMFCBaseTabCtrl::Serialize](#serialize)|從封存中讀取或寫入此物件。 (覆寫[CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CMFCBaseTabCtrl::SetActiveTab](#setactivetab)|啟動索引標籤。|  
|[CMFCBaseTabCtrl::SetActiveTabColor](#setactivetabcolor)|設定目前使用中之索引標籤的背景色彩。|  
|[CMFCBaseTabCtrl::SetActiveTabTextColor](#setactivetabtextcolor)|設定使用中索引標籤的文字色彩。|  
|[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)|設定自動色彩模式中套用的索引標籤控制項色彩。|  
|[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc)|設定適用於不從衍生的任何物件的包裝函式類別[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)。|  
|[CMFCBaseTabCtrl::SetDrawNoPrefix](#setdrawnoprefix)|啟用和停用當繪製索引標籤時處理前置詞字元。|  
|[CMFCBaseTabCtrl::SetImageList](#setimagelist)|設定圖示影像清單。|  
|[CMFCBaseTabCtrl::SetLocation](#setlocation)||  
|[CMFCBaseTabCtrl::SetTabBkColor](#settabbkcolor)|設定指定之索引標籤的背景色彩。|  
|[CMFCBaseTabCtrl::SetTabBorderSize](#settabbordersize)|設定新的索引標籤框線大小。|  
|[CMFCBaseTabCtrl::SetTabHicon](#settabhicon)|設定索引標籤圖示。|  
|[CMFCBaseTabCtrl::SetTabIcon](#settabicon)|設定索引標籤圖示識別碼。|  
|[CMFCBaseTabCtrl::SetTabIconOnly](#settabicononly)|啟用和停用指定之索引標籤的「僅圖示」模式。|  
|[CMFCBaseTabCtrl::SetTabLabel](#settablabel)|設定等於指定之字串值的索引標籤。|  
|[CMFCBaseTabCtrl::SetTabsHeight](#settabsheight)||  
|[CMFCBaseTabCtrl::SetTabTextColor](#settabtextcolor)|設定指定之索引標籤的文字色彩。|  
|[CMFCBaseTabCtrl::SetTabsOrder](#settabsorder)|依指定的順序排列索引標籤。|  
|[CMFCBaseTabCtrl::ShowTab](#showtab)|顯示或隱藏指定的索引標籤。|  
|[CMFCBaseTabCtrl::StartRenameTab](#startrenametab)||  
|[CMFCBaseTabCtrl::SwapTabs](#swaptabs)||  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)|建立包裝函式物件衍生自[CWnd](../../mfc/reference/cwnd-class.md) ，不衍生自`CDockablePane`。 若要停駐 `CMFCBaseTabCtrl` 物件，每個內嵌的控制項必須具有停駐的包裝函式或衍生自 `CDockablePane`。<br /><br /> 您可以使用 `SetDockingBayWrapperRTC`來設定包裝函式的類別。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::m_bActivateTabOnRightClick](#m_bactivatetabonrightclick)|指定選取索引標籤的方式是按一下滑鼠左鍵或是按一下滑鼠右鍵。|  
|[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)|指定是否自動終結索引標籤中包含的窗格。|  
  
## <a name="remarks"></a>備註  
 `CMFCBaseTabCtrl` 類別是抽象類別。 因此，無法具現化。 若要建立索引標籤式視窗，您必須從 `CMFCBaseTabCtrl`衍生類別。 MFC 程式庫包含一些在衍生的類別的範例，其中兩個是[CMFCTabCtrl 類別](../../mfc/reference/cmfctabctrl-class.md)和[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)。  
  
 從 [!INCLUDE[vs_dev14](../../ide/includes/vs_dev14_md.md)] 開始，這個類別支援 Microsoft Active Accessibility。  
  
## <a name="customization-tips"></a>自訂秘訣  
 下列秘訣屬於`CMFCBaseTabCtrl Class`以及任何從它繼承的類別︰  
  
-   如果您啟用可中斷連結的索引標籤，請不要保留索引標籤式視窗的指標。 您可以動態建立及終結這些可中斷連結的索引標籤。 因此，指標可能會變成無效。  
  
-   您可以設定索引標籤控制項，讓使用者可以使用滑鼠，在索引標籤控制項上動態移動索引標籤。 此功能內建至 `CMFCBaseTabCtrl` 類別。 若要啟用它，請呼叫[CMFCBaseTabCtrl::EnableTabSwap](#enabletabswap)。  
  
-   依預設，將索引標籤加入至索引標籤控制項時，即可中斷連結索引標籤。 您也可以藉由加入非可拆式索引標籤[CMFCBaseTabCtrl::AddTab](#addtab)。 如果您將參數 `bDetachable` 設為 `FALSE`，將無法中斷連結索引標籤。 您也可以變更是否索引標籤可分開的呼叫方法[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)。  
  
-   物件是衍生自[CWnd 類別](../../mfc/reference/cwnd-class.md)會放置在可停駐控制列或可停駐 索引標籤。 若要停駐整個控制項，您必須使 `CWnd` 成為可停駐的物件。 為了達成此目的，MFC 會使用包裝函式類別。 這個包裝函式類別是[CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md)。 任何加入至可停駐控制項列或可停駐索引標籤的 `CWnd` 物件將包裝在 `CDockablePaneAdapter` 物件內。 您可以藉由將 `m_bEnableWrapping` 物件的參數 `CMFCBaseTablCtrl` 設為 `FALSE`，來停用自動包裝。 您也可以變更您的應用程式使用的方法，將使用的包裝函式的類別[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxbasetabctrl.h  
  
##  <a name="a-nameaddicona--cmfcbasetabctrladdicon"></a><a name="addicon"></a>CMFCBaseTabCtrl::AddIcon  
 將圖示加入至清單中受保護的圖示`CMap``m_mapAddedIcons`成員。  
  
```  
void AddIcon(
    HICON hIcon,  
    int iIcon);
```  
  
### <a name="parameters"></a>參數  
 [in] `hIcon`  
 要加入之圖示的控制代碼。  
  
 [in] `iIcon`  
 以零起始的索引中受保護的圖示`CImageList``m_Images`成員。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddtaba--cmfcbasetabctrladdtab"></a><a name="addtab"></a>CMFCBaseTabCtrl::AddTab  
 將新的索引標籤加入至索引標籤控制項。  
  
```  
virtual void AddTab(
    CWnd* pTabWnd,  
    LPCTSTR lpszTabLabel,  
    UINT uiImageId = (UINT)-1,,  
    BOOL bDetachable = TRUE);

 
virtual void AddTab(
    CWnd* pTabWnd,  
    UINT uiResTabLabel,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pTabWnd`  
 這個方法表示為新的索引標籤視窗的指標。  
  
 [in] `lpszTabLabel`  
 字串，包含新的索引標籤的標籤。  
  
 [in] `uiImageId`  
 影像清單中的影像 ID。 索引標籤控制項當做圖示使用此映像，新索引標籤。  
  
 [in] `uiResTabLabel`  
 標籤的資源識別碼。  
  
 [in] `bDetachable`  
 判斷是否有新的索引標籤可分開的布林值參數。  
  
### <a name="remarks"></a>備註  
 如果`pTabWnd`指向的物件不衍生自[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)如果`bDetachable`是`TRUE`，架構會自動建立的包裝函式`pTabWnd`物件。 包裝函式可讓`pTabWnd`分離式的物件。 根據預設，包裝函式是執行個體[CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md)。 如果無法接受的預設包裝函式所提供的功能，請使用[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc)方法，以指定不同的包裝函式。  
  
##  <a name="a-nameapplyrestoredtabinfoa--cmfcbasetabctrlapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CMFCBaseTabCtrl::ApplyRestoredTabInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bUseTabIndexes`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameautodestroywindowa--cmfcbasetabctrlautodestroywindow"></a><a name="autodestroywindow"></a>CMFCBaseTabCtrl::AutoDestroyWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AutoDestroyWindow(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAutoDestroy`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecalcrectedita--cmfcbasetabctrlcalcrectedit"></a><a name="calcrectedit"></a>CMFCBaseTabCtrl::CalcRectEdit  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectEdit`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecleanupa--cmfcbasetabctrlcleanup"></a><a name="cleanup"></a>CMFCBaseTabCtrl::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CleanUp();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameclearimagelista--cmfcbasetabctrlclearimagelist"></a><a name="clearimagelist"></a>CMFCBaseTabCtrl::ClearImageList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ClearImageList();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecreatewrappera--cmfcbasetabctrlcreatewrapper"></a><a name="createwrapper"></a>CMFCBaseTabCtrl::CreateWrapper  
 建立衍生自的框架視窗的包裝函式[CWnd 類別](../../mfc/reference/cwnd-class.md)但不衍生自[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)。  
  
```  
virtual CWnd* CreateWrapper(
    CWnd* pWndToWrap,  
    LPCTSTR lpszTabLabel,  
    BOOL bDetachable);
```  
  
### <a name="parameters"></a>參數  
 [in] `pWndToWrap`  
 包裝框架視窗的指標。  
  
 [in] `lpszTabLabel`  
 字串，包含視窗的標籤。  
  
 [in] `bDetachable`  
 布林值的參數，指出視窗是否分離。  
  
### <a name="return-value"></a>傳回值  
 包裝函式的指標衍生自`CDockablePane`類別如果`CreateWrapper`成功建立包裝函式類別`pWndToWrap`。 如果方法失敗，它 retruns `pWndToWrap`。  
  
### <a name="remarks"></a>備註  
 索引標籤式的視窗可以停駐任何物件衍生自`CWnd`。 不過，為了讓`CMFCBaseTabCtrl Class`可停駐的物件，每個物件上的`CMFCBaseTabCtrl`必須是可分開。 因此，`CMFCBaseTabCtrl`會自動換行不從衍生的任何物件`CDockablePane`。  
  
 根據預設，`CMFCBaseTabCtrl`建立的執行個體[CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md)。 若要變更包裝函式的預設類別，請呼叫[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc)。  
  
 如果`pWndToWrap`衍生自`CDockablePane`，這個方法不會建立一個包裝函式。 相反地，它將會失敗，並傳回`pWndToWrap`。  
  
##  <a name="a-namedetachtaba--cmfcbasetabctrldetachtab"></a><a name="detachtab"></a>CMFCBaseTabCtrl::DetachTab  
 架構會呼叫此方法以中斷連結的索引標籤上，從索引標籤控制項。  
  
```  
virtual BOOL DetachTab(
    AFX_DOCK_METHOD dockMethod,  
    int nTabNum = -1,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `dockMethod`  
 列舉的資料類型所提供[CBasePane 類別](../../mfc/reference/cbasepane-class.md)。 此資料型別會指定用來卸離 索引標籤的方法。  
  
 [in] `nTabNum`  
 要卸離 索引標籤的以零為起始的索引。  
  
 [in] `bHide`  
 布林值的參數，指出架構是否應該隱藏 [中斷連結] 索引標籤。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果所指定的索引標籤`nTabNum`是非分離的此函式會失敗並傳回`FALSE`。  
  
##  <a name="a-nameenableactivatelastactivea--cmfcbasetabctrlenableactivatelastactive"></a><a name="enableactivatelastactive"></a>CMFCBaseTabCtrl::EnableActivateLastActive  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableActivateLastActive(BOOL bLastActive = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bLastActive`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenableautocolora--cmfcbasetabctrlenableautocolor"></a><a name="enableautocolor"></a>CMFCBaseTabCtrl::EnableAutoColor  
 控制是否架構會使用自動的背景色彩繪製一個索引標籤時。  
  
```  
void EnableAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值的參數會決定是否該架構會使用自動的色彩。  
  
### <a name="remarks"></a>備註  
 索引標籤控制項有數個預先定義之色彩的陣列。 架構會使用自動色彩，一系列的索引標籤中的每個索引標籤會從這個陣列中指派下一個色彩。  
  
 根據預設，自動色彩是由程式庫定義之色彩決定的。 您可以藉由呼叫提供的自訂色彩陣列[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)。  
  
##  <a name="a-nameenablecustomtooltipsa--cmfcbasetabctrlenablecustomtooltips"></a><a name="enablecustomtooltips"></a>CMFCBaseTabCtrl::EnableCustomToolTips  
 可讓自訂索引標籤控制項的工具提示。  
  
```  
BOOL EnableCustomToolTips(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值，決定是否要使用自訂的工具提示。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果啟用自訂的工具提示，就會傳送索引標籤控制項`AFX_WM_ON_GET_TAB_TOOLTIP`主框架的訊息。 如果您想要自訂的工具提示支援應用程式中，主框架視窗必須處理這個方法，並提供自訂的工具提示文字。 如需提供自訂的工具提示文字的詳細資訊，請參閱[CMFCTabToolTipInfo 結構](../../mfc/reference/cmfctabtooltipinfo-structure.md)。  
  
##  <a name="a-nameenableinplaceedita--cmfcbasetabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCBaseTabCtrl::EnableInPlaceEdit  
 可讓您直接編輯使用者 索引標籤的標籤。  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable) = 0;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值的參數，指定是否要啟用直接編輯索引標籤。  
  
### <a name="remarks"></a>備註  
 根據預設，直接編輯索引標籤會停用索引標籤控制項。  
  
 您可以啟用直接編輯索引標籤上的索引標籤控制項的子集。 若要這樣做，請覆寫方法`CMFCBaseTabCtrl::StartRenameTab`。 `StartRenameTab`應該會傳回非零值給支援直接編輯索引標籤的所有索引標籤。  
  
 在`CMFCBaseTabCtrl Class`，這個方法是純虛擬函式，而沒有實作。 如果衍生自`CMFCBaseTabCtrl`，您必須實作此函式。  
  
##  <a name="a-nameenabletabdetacha--cmfcbasetabctrlenabletabdetach"></a><a name="enabletabdetach"></a>CMFCBaseTabCtrl::EnableTabDetach  
 啟用可中斷連結的索引標籤。  
  
```  
virtual BOOL EnableTabDetach(
    int iTab,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
 [in] `bEnable`  
 布林值，指出是否要讓可拆式索引標籤。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
##  <a name="a-nameenabletabswapa--cmfcbasetabctrlenabletabswap"></a><a name="enabletabswap"></a>CMFCBaseTabCtrl::EnableTabSwap  
 可讓使用者變更定位順序，使用滑鼠。  
  
```  
void EnableTabSwap(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值，指出是否要啟用交換 索引標籤。  
  
### <a name="remarks"></a>備註  
 啟用索引標籤上交換時，使用者可以拖曳索引標籤，並變更其索引標籤控制項中的相對位置。  
  
##  <a name="a-nameensurevisiblea--cmfcbasetabctrlensurevisible"></a><a name="ensurevisible"></a>CMFCBaseTabCtrl::EnsureVisible  
 將索引標籤捲動直到看見指定的索引標籤。  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果所指示的索引標籤上，這個方法會有任何作用`iTab`已經看得見。  
  
 根據預設，這個方法不支援`CMFCBaseTabCtrl Class`。 您應該實作此函式中的自訂類別衍生自`CMFCBaseTabCtrl`如果該自訂索引標籤控制項支援捲動 索引標籤。 這個方法支援[CMFCTabCtrl 類別](../../mfc/reference/cmfctabctrl-class.md)。  
  
##  <a name="a-nameenterdragmodea--cmfcbasetabctrlenterdragmode"></a><a name="enterdragmode"></a>CMFCBaseTabCtrl::EnterDragMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnterDragMode();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namefindtargetwnda--cmfcbasetabctrlfindtargetwnd"></a><a name="findtargetwnd"></a>CMFCBaseTabCtrl::FindTargetWnd  
 識別包含指定的點的窗格。  
  
```  
virtual CWnd* FindTargetWnd(const CPoint& pt) = 0;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pt`  
 藉由使用用戶端區域定義的點座標[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)物件如果成功，否則為`NULL`。  
  
### <a name="remarks"></a>備註  
 在`CMFCBaseTabCtrl`類別，這個方法是純虛擬函式︰ 必須先實作衍生自如果`CMFCBaseTabCtrl`。  
  
##  <a name="a-namefirechangeactivetaba--cmfcbasetabctrlfirechangeactivetab"></a><a name="firechangeactivetab"></a>CMFCBaseTabCtrl::FireChangeActiveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void FireChangeActiveTab(int nNewTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `nNewTab`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namefirechangingactivetaba--cmfcbasetabctrlfirechangingactivetab"></a><a name="firechangingactivetab"></a>CMFCBaseTabCtrl::FireChangingActiveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL FireChangingActiveTab(int nNewTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `nNewTab`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetactivetaba--cmfcbasetabctrlgetactivetab"></a><a name="getactivetab"></a>CMFCBaseTabCtrl::GetActiveTab  
 擷取目前作用中 索引標籤的索引。  
  
```  
virtual int GetActiveTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 以零起始的索引的使用中的索引標籤。如果沒有任何作用中索引標籤，為-1。  
  
##  <a name="a-namegetactivetabcolora--cmfcbasetabctrlgetactivetabcolor"></a><a name="getactivetabcolor"></a>CMFCBaseTabCtrl::GetActiveTabColor  
 擷取目前作用中 索引標籤的背景色彩。  
  
```  
virtual COLORREF GetActiveTabColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，指定 [作用中] 索引標籤的背景色彩。  
  
### <a name="remarks"></a>備註  
 根據預設，作用中的索引標籤的背景色彩是`COLOR_WINDOW`。 您可以使用的方法來變更 [使用中] 索引標籤的背景色彩[CMFCBaseTabCtrl::SetActiveTabColor](#setactivetabcolor)。  
  
##  <a name="a-namegetactivetabtextcolora--cmfcbasetabctrlgetactivetabtextcolor"></a><a name="getactivetabtextcolor"></a>CMFCBaseTabCtrl::GetActiveTabTextColor  
 擷取使用中的索引標籤的文字色彩。  
  
```  
virtual COLORREF GetActiveTabTextColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，指定 [作用中] 索引標籤的文字色彩。  
  
### <a name="remarks"></a>備註  
 根據預設，是使用中的索引標籤的文字色彩`COLOR_WINDOWTEXT`。 您可以使用此方法來變更文字色彩[CMFCBaseTabCtrl::SetActiveTabTextColor](#setactivetabtextcolor)。  
  
##  <a name="a-namegetactivewnda--cmfcbasetabctrlgetactivewnd"></a><a name="getactivewnd"></a>CMFCBaseTabCtrl::GetActiveWnd  
 擷取目前作用中 索引標籤視窗的指標。  
  
```  
virtual CWnd* GetActiveWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 視窗的指標。  
  
##  <a name="a-namegetautocolorsa--cmfcbasetabctrlgetautocolors"></a><a name="getautocolors"></a>CMFCBaseTabCtrl::GetAutoColors  
 擷取用於自動上色色彩的陣列。  
  
```  
const CArray<COLORREF,COLORREF>& GetAutoColors() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列的參考[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)物件可使用自動定位著色。  
  
### <a name="remarks"></a>備註  
 根據預設，架構會初始化陣列的程式庫定義之色彩的色彩。 您可以藉由呼叫此方法提供色彩的自訂陣列[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)。  
  
##  <a name="a-namegetfirstvisibletaba--cmfcbasetabctrlgetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CMFCBaseTabCtrl::GetFirstVisibleTab  
 擷取第一個可見的索引標籤的指標。  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);

 
virtual CWnd* GetFirstVisibleTab(
    int iStartFrom,  
    int& iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `iTabNum`  
 整數的參考。 這個方法會寫入此參數中的第一個可見的索引標籤的以零為起始的索引。  
  
 [in] `iStartFrom`  
 第一個索引標籤，來檢查以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 第一個可見的定位成功; 如果指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
 如果此方法失敗，它會寫入到的值為-1 `iStartFrom`。  
  
 如果`iStartFrom`是大於或等於 索引標籤控制項索引標籤數目`GetFirstVisibleTab`自動失敗。  
  
##  <a name="a-namegetfirstvisibletabnuma--cmfcbasetabctrlgetfirstvisibletabnum"></a><a name="getfirstvisibletabnum"></a>CMFCBaseTabCtrl::GetFirstVisibleTabNum  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegethighlightedtaba--cmfcbasetabctrlgethighlightedtab"></a><a name="gethighlightedtab"></a>CMFCBaseTabCtrl::GetHighlightedTab  
 擷取目前反白顯示 索引標籤的索引。  
  
```  
int GetHighlightedTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 反白顯示 索引標籤的以零為起始的索引。  
  
##  <a name="a-namegetimagelista--cmfcbasetabctrlgetimagelist"></a><a name="getimagelist"></a>CMFCBaseTabCtrl::GetImageList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual const CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetimagesizea--cmfcbasetabctrlgetimagesize"></a><a name="getimagesize"></a>CMFCBaseTabCtrl::GetImageSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlastvisibletaba--cmfcbasetabctrlgetlastvisibletab"></a><a name="getlastvisibletab"></a>CMFCBaseTabCtrl::GetLastVisibleTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CWnd* GetLastVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTabNum`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlocationa--cmfcbasetabctrlgetlocation"></a><a name="getlocation"></a>CMFCBaseTabCtrl::GetLocation  
 擷取的索引標籤區域部分的索引標籤控制項的位置。  
  
```  
Location GetLocation() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤區域位置。  
  
### <a name="remarks"></a>備註  
 可能的索引標籤區域位置的值為`LOCATION_BOTTOM`和`LOCATION_TOP`。  
  
##  <a name="a-namegetmaxwindowsizea--cmfcbasetabctrlgetmaxwindowsize"></a><a name="getmaxwindowsize"></a>CMFCBaseTabCtrl::GetMaxWindowSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetMaxWindowSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabareaa--cmfcbasetabctrlgettabarea"></a><a name="gettabarea"></a>CMFCBaseTabCtrl::GetTabArea  
 擷取的大小和位置的索引標籤控制項的索引標籤區域。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>參數  
 [in] `rectTabAreaTop`  
 對 `CRect` 物件的參考。 `GetTabArea`使用此物件存放區的大小和最上層索引標籤區域位置。  
  
 [in] `rectTabAreaBottom`  
 對 `CRect` 物件的參考。 `GetTabArea`使用此物件存放區的大小和下方的索引標籤區域位置。  
  
### <a name="remarks"></a>備註  
 之後`GetTabArea`傳回，`CRect`參數包含的大小和索引標籤控制項的用戶端座標中的索引標籤區域位置。 如果沒有頂端或底部的索引標籤控制項中，不含索引標籤區域`rectTabAreaTop`或`rectTabAreaBottom`是空的。  
  
 在`CMFCBaseTabCtrl Class`，這個方法是純虛擬函式，而沒有實作。 如果衍生自`CMFCBaseTabCtrl`，您必須實作此函式。  
  
##  <a name="a-namegettabbkcolora--cmfcbasetabctrlgettabbkcolor"></a><a name="gettabbkcolor"></a>CMFCBaseTabCtrl::GetTabBkColor  
 擷取指定的索引標籤的背景色彩。  
  
```  
virtual COLORREF GetTabBkColor(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，指出指定的索引標籤的背景色彩，則為-1 表示`iTab`超出範圍。  
  
##  <a name="a-namegettabbordersizea--cmfcbasetabctrlgettabbordersize"></a><a name="gettabbordersize"></a>CMFCBaseTabCtrl::GetTabBorderSize  
 擷取索引標籤控制項中的索引標籤框線的大小。  
  
```  
virtual int GetTabBorderSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤的框線，單位為像素的大小。  
  
### <a name="remarks"></a>備註  
 索引標籤框線的預設大小為三個像素。 您可以使用的方法來變更此框線大小[CMFCBaseTabCtrl::SetTabBorderSize](#settabbordersize)。  
  
##  <a name="a-namegettabbyida--cmfcbasetabctrlgettabbyid"></a><a name="gettabbyid"></a>CMFCBaseTabCtrl::GetTabByID  
 擷取索引標籤，根據索引標籤識別碼。  
  
```  
virtual int GetTabByID(int id) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `id`  
 索引標籤識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果找到; 索引標籤的以零起始的索引如果找不到索引標籤識別碼-1。  
  
### <a name="remarks"></a>備註  
 [] 索引標籤 Id 會自動指派索引標籤加入至索引標籤控制項時。  
  
##  <a name="a-namegettabclosebuttona--cmfcbasetabctrlgettabclosebutton"></a><a name="gettabclosebutton"></a>CMFCBaseTabCtrl::GetTabCloseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetTabCloseButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabfromhwnda--cmfcbasetabctrlgettabfromhwnd"></a><a name="gettabfromhwnd"></a>CMFCBaseTabCtrl::GetTabFromHwnd  
 擷取包含指定的 HWND 物件的索引標籤的索引。  
  
```  
virtual int GetTabFromHwnd(HWND hwnd) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `hwnd`  
 視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則 索引標籤的以零起始的索引-1，如果沒有索引標籤包含`hwnd`。  
  
##  <a name="a-namegettabfrompointa--cmfcbasetabctrlgettabfrompoint"></a><a name="gettabfrompoint"></a>CMFCBaseTabCtrl::GetTabFromPoint  
 擷取包含指定的點的索引標籤。  
  
```  
virtual int GetTabFromPoint(CPoint& pt) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pt`  
 用戶端座標中的索引標籤控制項的點。  
  
### <a name="return-value"></a>傳回值  
 索引標籤，其中包含的索引`pt`;-1，如果沒有索引標籤包含`pt`。  
  
##  <a name="a-namegettabfullwidtha--cmfcbasetabctrlgettabfullwidth"></a><a name="gettabfullwidth"></a>CMFCBaseTabCtrl::GetTabFullWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabFullWidth(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabhicona--cmfcbasetabctrlgettabhicon"></a><a name="gettabhicon"></a>CMFCBaseTabCtrl::GetTabHicon  
 傳回與指定的索引標籤相關聯的 HICON。  
  
```  
virtual HICON GetTabHicon(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 索引標籤標籤成功; 如果相關聯的 HICON`NULL`如果沒有任何 HICON，或如果方法失敗。  
  
##  <a name="a-namegettabicona--cmfcbasetabctrlgettabicon"></a><a name="gettabicon"></a>CMFCBaseTabCtrl::GetTabIcon  
 擷取與指定的索引標籤相關聯的圖示。  
  
```  
virtual UINT GetTabIcon(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 圖示 ID 指定的索引標籤，如果登錄成功。如果索引是無效的-1。  
  
### <a name="remarks"></a>備註  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)物件儲存在內部圖示[CImageList](../../mfc/reference/cimagelist-class.md)物件。  
  
##  <a name="a-namegettabida--cmfcbasetabctrlgettabid"></a><a name="gettabid"></a>CMFCBaseTabCtrl::GetTabID  
 擷取識別碼索引標籤索引所指定的索引標籤。  
  
```  
int GetTabID(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 識別碼為 [] 索引標籤或-1 表示`iTab`超出範圍。  
  
##  <a name="a-namegettablabela--cmfcbasetabctrlgettablabel"></a><a name="gettablabel"></a>CMFCBaseTabCtrl::GetTabLabel  
 擷取的索引標籤的標籤文字。  
  
```  
virtual BOOL GetTabLabel(
    int iTab,  
    CString& strLabel) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
 [輸出] `strLabel`  
 對 `CString` 物件的參考。 此方法將此參數中儲存的索引標籤。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 如果索引`iTab`不正確。  
  
 當您使用 [建立] 索引標籤，設定索引標籤的標籤[CMFCBaseTabCtrl::AddTab](#addtab)。 您也可以變更之後建立標籤，使用方法[CMFCBaseTabCtrl::SetTabLabel](#settablabel)。  
  
##  <a name="a-namegettabrecta--cmfcbasetabctrlgettabrect"></a><a name="gettabrect"></a>CMFCBaseTabCtrl::GetTabRect  
 擷取指定的索引標籤的位置與大小。  
  
```  
virtual BOOL GetTabRect(
    int iTab,  
    CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
 [輸出] `rect`  
 對 `CRect` 物件的參考。 此方法將此參數中儲存的大小和位置 索引標籤。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FALSE`如果定位點索引無效。  
  
##  <a name="a-namegettabsheighta--cmfcbasetabctrlgettabsheight"></a><a name="gettabsheight"></a>CMFCBaseTabCtrl::GetTabsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabsnuma--cmfcbasetabctrlgettabsnum"></a><a name="gettabsnum"></a>CMFCBaseTabCtrl::GetTabsNum  
 擷取索引標籤控制項中的索引標籤的數目。  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤控制項中的標籤數目。  
  
##  <a name="a-namegettabsrecta--cmfcbasetabctrlgettabsrect"></a><a name="gettabsrect"></a>CMFCBaseTabCtrl::GetTabsRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `rect`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettabtextcolora--cmfcbasetabctrlgettabtextcolor"></a><a name="gettabtextcolor"></a>CMFCBaseTabCtrl::GetTabTextColor  
 擷取指定的索引標籤的文字色彩。  
  
```  
virtual COLORREF GetTabTextColor(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，指出指定的索引標籤的文字色彩，則為-1 表示`iTab`超出範圍。  
  
##  <a name="a-namegettabwnda--cmfcbasetabctrlgettabwnd"></a><a name="gettabwnd"></a>CMFCBaseTabCtrl::GetTabWnd  
 傳回位於指定的索引標籤的窗格的指標。  
  
```  
virtual CWnd* GetTabWnd(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)位於 [] 索引標籤的物件，`iTab`指定。 `NULL`如果`iTab`不正確。  
  
### <a name="remarks"></a>備註  
 傳回的物件是此應用程式加入時呼叫該方法是一個[CMFCBaseTabCtrl::AddTab](#addtab)或[CMFCBaseTabCtrl::InsertTab](#inserttab)。  
  
 如果索引標籤上的物件有一個包裝函式，這個方法會傳回物件的包裝函式。 如需包裝函式的詳細資訊，請參閱[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)。 如果您想要存取直接物件，而不需要包裝函式的指標，使用方法[CMFCBaseTabCtrl::GetTabWndNoWrapper](#gettabwndnowrapper)。  
  
##  <a name="a-namegettabwndnowrappera--cmfcbasetabctrlgettabwndnowrapper"></a><a name="gettabwndnowrapper"></a>CMFCBaseTabCtrl::GetTabWndNoWrapper  
 傳回的指標位於索引標籤中的控制項，即使控制項有包裝函式。  
  
```  
virtual CWnd* GetTabWndNoWrapper(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)物件位於指定的索引標籤。`NULL`如果`iTab`不正確。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取直接指向`CWnd`物件您藉由使用這兩種方法中新增[CMFCBaseTabCtrl::AddTab](#addtab)或[CMFCBaseTabCtrl::InsertTab](#inserttab)。 `GetTabWndNoWrapper`將擷取的指標，加入的`CWnd`，即使架構加入物件的包裝函式。 如需有關包裝函式和[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)，請參閱[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)。  
  
 使用方法[CMFCBaseTabCtrl::GetTabWnd](#gettabwnd)若不想忽略包裝函式類別。  
  
##  <a name="a-namegettooltipctrla--cmfcbasetabctrlgettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCBaseTabCtrl::GetToolTipCtrl  
 擷取工具提示 contorl 的參考。  
  
```  
CToolTipCtrl& GetToolTipCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 工具提示控制項的參考。  
  
##  <a name="a-namegetvisibletabsnuma--cmfcbasetabctrlgetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CMFCBaseTabCtrl::GetVisibleTabsNum  
 擷取目前可見的標籤數目。  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 可見的標籤數目。  
  
##  <a name="a-namehasimagea--cmfcbasetabctrlhasimage"></a><a name="hasimage"></a>CMFCBaseTabCtrl::HasImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasImage(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namehidesingletaba--cmfcbasetabctrlhidesingletab"></a><a name="hidesingletab"></a>CMFCBaseTabCtrl::HideSingleTab  
 設定要顯示索引標籤時隱藏 索引標籤控制項的索引標籤的選項。  
  
```  
virtual void HideSingleTab(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHide`  
 布林值，指定是否啟用隱藏單一索引標籤。  
  
### <a name="remarks"></a>備註  
 您的應用程式設定為隱藏單一索引標籤中，架構的第二個索引標籤新增至索引標籤控制項時，會自動顯示索引標籤。  
  
##  <a name="a-nameinserttaba--cmfcbasetabctrlinserttab"></a><a name="inserttab"></a>CMFCBaseTabCtrl::InsertTab  
 插入索引標籤控制項 索引標籤。  
  
```  
Virtual void InsertTab(
    CWnd* pNewWnd,  
    LPCTSTR lpszTabLabel,  
    int nInsertAt,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);

 
virtual void InsertTab(
    CWnd* pNewWnd,  
    UINT uiResTabLabel,  
    int nInsertAt,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pNewWnd`  
 這個方法會加入成為新的索引標籤視窗的指標。  
  
 [in] `lpszTabLabel`  
 字串，包含新的索引標籤的標籤。  
  
 [in] `nInsertAt`  
 新的索引標籤以零為起始的索引。  
  
 [in] `uiImageId`  
 影像清單中的影像 ID。 索引標籤控制項當做圖示使用此映像，新索引標籤。  
  
 [in] `bDetachable`  
 判斷是否有新的索引標籤可分開的布林值參數。  
  
 [in] `uiResTabLabel`  
 標籤的資源識別碼。  
  
### <a name="remarks"></a>備註  
 如果物件由`pNewWnd`不衍生自[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)如果`bDetachable`參數是`TRUE`，架構就會建立新的索引標籤的特殊包裝函式。 根據預設，包裝函式是執行個體[CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md)。 使用[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc)方法來建立不同的包裝函式類別。 任何自訂包裝函式類別必須衍生自`CDockablePaneAdapter`。  
  
##  <a name="a-nameinvalidatetaba--cmfcbasetabctrlinvalidatetab"></a><a name="invalidatetab"></a>CMFCBaseTabCtrl::InvalidateTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void InvalidateTab(int iTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisactivetabclosebuttona--cmfcbasetabctrlisactivetabclosebutton"></a><a name="isactivetabclosebutton"></a>CMFCBaseTabCtrl::IsActiveTabCloseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisautocolora--cmfcbasetabctrlisautocolor"></a><a name="isautocolor"></a>CMFCBaseTabCtrl::IsAutoColor  
 決定索引標籤控制項是否處於 autocolor 模式。  
  
```  
BOOL IsAutoColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤控制項處於 autocolor 模式;`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 您可以啟用或停用 autocolor 模式使用[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)方法。  
  
##  <a name="a-nameisautodestroywindowa--cmfcbasetabctrlisautodestroywindow"></a><a name="isautodestroywindow"></a>CMFCBaseTabCtrl::IsAutoDestroyWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAutoDestroyWindow() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameiscoloreda--cmfcbasetabctrliscolored"></a><a name="iscolored"></a>CMFCBaseTabCtrl::IsColored  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsColored() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdialogcontrola--cmfcbasetabctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCBaseTabCtrl::IsDialogControl  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdrawnoprefixa--cmfcbasetabctrlisdrawnoprefix"></a><a name="isdrawnoprefix"></a>CMFCBaseTabCtrl::IsDrawNoPrefix  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDrawNoPrefix() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisflatframea--cmfcbasetabctrlisflatframe"></a><a name="isflatframe"></a>CMFCBaseTabCtrl::IsFlatFrame  
 指出中平面樣式或 3D 樣式中，是否要呈現的框架 索引標籤控制項。  
  
```  
virtual BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤控制項的框架會轉譯成平面式;`FALSE`如果畫面格呈現 3D 樣式。  
  
### <a name="remarks"></a>備註  
 使用[CMFCTabCtrl::SetFlatFrame](../../mfc/reference/cmfctabctrl-class.md#setflatframe)變更框架 索引標籤控制項的樣式。  
  
 使用 Outlook 樣式的索引標籤控制項，都無法使用一般的畫面格呈現。 這包括[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)以及衍生自該類別的任何類別。  
  
##  <a name="a-nameisflattaba--cmfcbasetabctrlisflattab"></a><a name="isflattab"></a>CMFCBaseTabCtrl::IsFlatTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameishidesingletaba--cmfcbasetabctrlishidesingletab"></a><a name="ishidesingletab"></a>CMFCBaseTabCtrl::IsHideSingleTab  
 決定是否只有一個索引標籤索引標籤控制項是否會隱藏 索引標籤的標籤。  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤控制項隱藏 索引標籤的標籤，當它有一個索引標籤。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用方法[CMFCBaseTabCtrl::HideSingleTab](#hidesingletab)啟用只有一個索引標籤時隱藏 索引標籤的標籤。  
  
##  <a name="a-nameisiconaddeda--cmfcbasetabctrlisiconadded"></a><a name="isiconadded"></a>CMFCBaseTabCtrl::IsIconAdded  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsIconAdded(
    HICON hIcon,  
    int& iIcon);
```  
  
### <a name="parameters"></a>參數  
 [in] `hIcon`  
 [in] `iIcon`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisinplaceedita--cmfcbasetabctrlisinplaceedit"></a><a name="isinplaceedit"></a>CMFCBaseTabCtrl::IsInPlaceEdit  
 指出是否設定索引標籤控制項可讓使用者動態修改索引標籤。  
  
```  
virtual BOOL IsInPlaceEdit() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果就地編輯已啟用。否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以啟用或停用就地編輯呼叫的方法來[CMFCBaseTabCtrl::EnableInPlaceEdit](#enableinplaceedit)。  
  
##  <a name="a-nameisleftrightroundeda--cmfcbasetabctrlisleftrightrounded"></a><a name="isleftrightrounded"></a>CMFCBaseTabCtrl::IsLeftRightRounded  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameismditaba--cmfcbasetabctrlismditab"></a><a name="ismditab"></a>CMFCBaseTabCtrl::IsMDITab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMDITab() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisonenotestylea--cmfcbasetabctrlisonenotestyle"></a><a name="isonenotestyle"></a>CMFCBaseTabCtrl::IsOneNoteStyle  
 決定標籤是否會顯示在 Microsoft OneNote 的樣式。  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤會顯示在 Microsoft onenote; 樣式否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫方法[CMDIFrameWndEx::EnableMDITabs](../../mfc/reference/cmdiframewndex-class.md#enablemditabs)啟用 Microsoft OneNote 樣式。 您也可以啟用此樣式，當您具現化[CMFCTabCtrl 類別](../../mfc/reference/cmfctabctrl-class.md)︰ 只要傳遞至方法的 樣式 STYLE_3D_ONENOTE [CMFCTabCtrl::Create](../../mfc/reference/cmfctabctrl-class.md#create)。  
  
 根據預設，Microsoft OneNote 樣式中不支援自訂類別衍生自`CMFCBaseTabCtrl Class`。 不過，在支援`CMFCTabCtrl`類別。  
  
##  <a name="a-nameisptintabareaa--cmfcbasetabctrlisptintabarea"></a><a name="isptintabarea"></a>CMFCBaseTabCtrl::IsPtInTabArea  
 決定在索引標籤區域內時點。  
  
```  
virtual BOOL IsPtInTabArea(CPoint point) const = 0;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 要測試的點。  
  
### <a name="return-value"></a>傳回值  
 非零，如果點 索引標籤區域中。否則為 0。  
  
### <a name="remarks"></a>備註  
 在`CMFCBaseTabCtrl Class`，這個方法是純虛擬函式，而沒有實作。 如果衍生自`CMFCBaseTabCtrl`，您必須實作此函式。  
  
##  <a name="a-nameistabclosebuttonhighlighteda--cmfcbasetabctrlistabclosebuttonhighlighted"></a><a name="istabclosebuttonhighlighted"></a>CMFCBaseTabCtrl::IsTabCloseButtonHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsTabCloseButtonHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameistabclosebuttonpresseda--cmfcbasetabctrlistabclosebuttonpressed"></a><a name="istabclosebuttonpressed"></a>CMFCBaseTabCtrl::IsTabCloseButtonPressed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsTabCloseButtonPressed() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameistabdetachablea--cmfcbasetabctrlistabdetachable"></a><a name="istabdetachable"></a>CMFCBaseTabCtrl::IsTabDetachable  
 判斷是否可拆式索引標籤。  
  
```  
virtual BOOL IsTabDetachable(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 若要檢查 索引標籤的以零起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤可分開。`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 若要分離式標籤，請使用方法[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)。  
  
##  <a name="a-nameistabicononlya--cmfcbasetabctrlistabicononly"></a><a name="istabicononly"></a>CMFCBaseTabCtrl::IsTabIconOnly  
 判斷是否要只有圖示和文字不包含索引標籤的標籤。  
  
```  
virtual BOOL IsTabIconOnly(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 索引標籤的標籤，且只有圖示;`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 若要設定您的應用程式顯示只有圖示索引標籤，呼叫方法[CMFCBaseTabCtrl::SetTabIconOnly](#settabicononly)。  
  
##  <a name="a-nameistabswapenableda--cmfcbasetabctrlistabswapenabled"></a><a name="istabswapenabled"></a>CMFCBaseTabCtrl::IsTabSwapEnabled  
 決定索引標籤控制項是否允許使用者使用滑鼠變更定位點位置。  
  
```  
BOOL IsTabSwapEnabled() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果定位點位置可以變更使用者資訊。否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，使用者無法變更索引標籤控制項中的索引標籤的順序。 使用[CMFCBaseTabCtrl::EnableTabSwap](#enabletabswap)方法，以啟用這項功能。  
  
##  <a name="a-nameistabvisiblea--cmfcbasetabctrlistabvisible"></a><a name="istabvisible"></a>CMFCBaseTabCtrl::IsTabVisible  
 指出指定的索引標籤是否可見。  
  
```  
virtual BOOL IsTabVisible(int iTab) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 若要檢查 索引標籤的以零起始的索引。  
  
### <a name="return-value"></a>傳回值  
 非零，如果指定的索引標籤是可見的。否則為 0。  
  
##  <a name="a-nameisvs2005stylea--cmfcbasetabctrlisvs2005style"></a><a name="isvs2005style"></a>CMFCBaseTabCtrl::IsVS2005Style  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namembactivatetabonrightclicka--cmfcbasetabctrlmbactivatetabonrightclick"></a><a name="m_bactivatetabonrightclick"></a>CMFCBaseTabCtrl::m_bActivateTabOnRightClick  
 `m_bActivateTabOnRightClick`決定當使用者使用滑鼠右鍵按一下索引標籤的標籤是否焦點的索引標籤。  
  
```  
BOOL m_bActivateTabOnRightClick;  
```  
  
### <a name="remarks"></a>備註  
 此資料成員的預設值是`FALSE`。  
  
##  <a name="a-namembautodestroywindowa--cmfcbasetabctrlmbautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCBaseTabCtrl::m_bAutoDestroyWindow  
 `m_bAutoDestroyWindow`決定移除索引標籤時是否架構會自動終結 索引標籤上的物件。  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>備註  
 根據預設，這個成員是`FALSE`。  
  
##  <a name="a-namemovetaba--cmfcbasetabctrlmovetab"></a><a name="movetab"></a>CMFCBaseTabCtrl::MoveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void MoveTab(
    int nSource,  
    int nDest);
```  
  
### <a name="parameters"></a>參數  
 [in] `nSource`  
 [in] `nDest`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonchangetabsa--cmfcbasetabctrlonchangetabs"></a><a name="onchangetabs"></a>CMFCBaseTabCtrl::OnChangeTabs  
 當控制項的索引標籤上的索引標籤的數目變更時，架構會呼叫這個方法。  
  
```  
virtual void OnChangeTabs();
```  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法沒有作用。 覆寫這個方法，以控制項的索引標籤上的索引標籤的數目變更時執行自訂程式碼。  
  
##  <a name="a-nameondropa--cmfcbasetabctrlondrop"></a><a name="ondrop"></a>CMFCBaseTabCtrl::OnDrop  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnDrop(
    COleDataObject*,
    DROPEFFECT,
    CPoint);
```  
  
### <a name="parameters"></a>參數  
 [in] `COleDataObject*`  
 [in] `DROPEFFECT`  
 [in] `CPoint`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondragovera--cmfcbasetabctrlondragover"></a><a name="ondragover"></a>CMFCBaseTabCtrl::OnDragOver  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject*,
    DWORD,
    CPoint);
```  
  
### <a name="parameters"></a>參數  
 [in] `COleDataObject*`  
 [in] `DWORD`  
 [in] `CPoint`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondragleavea--cmfcbasetabctrlondragleave"></a><a name="ondragleave"></a>CMFCBaseTabCtrl::OnDragLeave  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondragentera--cmfcbasetabctrlondragenter"></a><a name="ondragenter"></a>CMFCBaseTabCtrl::OnDragEnter  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject*,
    DWORD,
    CPoint);
```  
  
### <a name="parameters"></a>參數  
 [in] `COleDataObject*`  
 [in] `DWORD`  
 [in] `CPoint`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonrenametaba--cmfcbasetabctrlonrenametab"></a><a name="onrenametab"></a>CMFCBaseTabCtrl::OnRenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnRenameTab(int, CString&);
```  
  
### <a name="parameters"></a>參數  
 [in] `int`  
 [in] `CString&`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namepretranslatemessagea--cmfcbasetabctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCBaseTabCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [in] `pMsg`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namerecalclayouta--cmfcbasetabctrlrecalclayout"></a><a name="recalclayout"></a>CMFCBaseTabCtrl::RecalcLayout  
 重新計算索引標籤控制項的內部配置。  
  
```  
virtual void RecalcLayout() = 0;  
```  
  
### <a name="remarks"></a>備註  
 在`CMFCBaseTabCtrl Class`，這個方法是純虛擬函式。 如果衍生自`CMFCBaseTabCtrl`，您必須實作此函式。  
  
##  <a name="a-nameremovealltabsa--cmfcbasetabctrlremovealltabs"></a><a name="removealltabs"></a>CMFCBaseTabCtrl::RemoveAllTabs  
 從索引標籤控制項移除所有索引標籤。  
  
```  
virtual void RemoveAllTabs();
```  
  
### <a name="remarks"></a>備註  
 如果[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)是`TRUE`，架構會刪除所有[CWnd](../../mfc/reference/cwnd-class.md)物件附加至已移除的索引標籤。  
  
##  <a name="a-nameremovetaba--cmfcbasetabctrlremovetab"></a><a name="removetab"></a>CMFCBaseTabCtrl::RemoveTab  
 移除索引標籤控制項 索引標籤。  
  
```  
virtual BOOL RemoveTab(
    int iTab,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
 [in] `bRecalcLayout`  
 布林值的參數，指定是否要重新計算 索引標籤的配置。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果方法成功，會移除 [] 索引標籤否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)是`TRUE`，`RemoveTab`終結[CWnd](../../mfc/reference/cwnd-class.md)與指定的索引標籤相關聯的物件。  
  
##  <a name="a-namerenametaba--cmfcbasetabctrlrenametab"></a><a name="renametab"></a>CMFCBaseTabCtrl::RenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL RenameTab();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameresetimagelista--cmfcbasetabctrlresetimagelist"></a><a name="resetimagelist"></a>CMFCBaseTabCtrl::ResetImageList  
 重設執行個體的映像清單[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
```  
void ResetImageList();
```  
  
##  <a name="a-nameserializea--cmfcbasetabctrlserialize"></a><a name="serialize"></a>CMFCBaseTabCtrl::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [in] `ar`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetactivetaba--cmfcbasetabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCBaseTabCtrl::SetActiveTab  
 啟動指定的索引標籤。  
  
```  
virtual BOOL SetActiveTab(int iTab) = 0;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。 `SetActiveTab`將與這個索引標籤設為作用中。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 在`CMFCBaseTabCtrl Class`，這個方法是純虛擬函式。 如果衍生自`CMFCBaseTabCtrl`，您必須實作此函式。  
  
##  <a name="a-namesetactivetabcolora--cmfcbasetabctrlsetactivetabcolor"></a><a name="setactivetabcolor"></a>CMFCBaseTabCtrl::SetActiveTabColor  
 設定作用中的索引標籤的背景色彩。  
  
```  
virtual void SetActiveTabColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 [in] `clr`  
 指定新的背景色彩。  
  
### <a name="remarks"></a>備註  
 架構會取得從使用中的索引標籤的預設背景色彩[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)方法。  
  
##  <a name="a-namesetactivetabtextcolora--cmfcbasetabctrlsetactivetabtextcolor"></a><a name="setactivetabtextcolor"></a>CMFCBaseTabCtrl::SetActiveTabTextColor  
 設定使用中索引標籤的文字色彩。  
  
```  
virtual void SetActiveTabTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 [in] `clr`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，指定新的文字色彩。  
  
### <a name="remarks"></a>備註  
 根據預設，架構會取得文字的色彩[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)。 使用覆寫這個預設色彩`SetActiveTabTextColor`方法。  
  
##  <a name="a-namesetautocolorsa--cmfcbasetabctrlsetautocolors"></a><a name="setautocolors"></a>CMFCBaseTabCtrl::SetAutoColors  
 設定自動色彩模式中的架構會使用索引標籤控制項的色彩。  
  
```  
void SetAutoColors(const CArray<COLORREF,COLORREF>& arColors);
```  
  
### <a name="parameters"></a>參數  
 [in] `arColors`  
 RGB 色彩的陣列。  
  
### <a name="remarks"></a>備註  
 如果您提供的自訂色彩陣列時，會忽略色彩預設陣列。 如果參數`arColors`是空的架構會還原成預設值陣列的色彩。  
  
 若要啟用 autocolor 模式，請使用[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)方法。  
  
##  <a name="a-namesetdockingbarwrapperrtca--cmfcbasetabctrlsetdockingbarwrapperrtc"></a><a name="setdockingbarwrapperrtc"></a>CMFCBaseTabCtrl::SetDockingBarWrapperRTC  
 設定適用於不從衍生的任何物件的包裝函式類別[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)。  
  
```  
void SetDockingBarWrapperRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pRTC`  
 新的包裝函式類別的執行階段類別資訊。  
  
### <a name="remarks"></a>備註  
 使用兩種方式新增索引標籤控制項索引標籤[CMFCBaseTabCtrl::AddTab](#addtab)和[CMFCBaseTabCtrl::InsertTab](#inserttab)。 當您加入的索引標籤時，在該索引標籤上的每個控制項必須是可停駐。 不從衍生的任何物件`CDockablePane`必須包裝。 `AddTab`和`InsertTab`建立這些物件的包裝函式。 預設包裝函式類別是[CDockablePaneAdapter 類別](../../mfc/reference/cdockablepaneadapter-class.md)。 此方法`SetDockingBarWrapperRTC`可讓您變更做為包裝函式類別的類別。 您提供的包裝函式類別必須衍生自`CDockablePaneAdapter`。  
  
##  <a name="a-namesetdrawnoprefixa--cmfcbasetabctrlsetdrawnoprefix"></a><a name="setdrawnoprefix"></a>CMFCBaseTabCtrl::SetDrawNoPrefix  
 啟用和停用的索引標籤中的前置詞字元處理。  
  
```  
void SetDrawNoPrefix(
    BOOL bNoPrefix,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bNoPrefix`  
 `TRUE`如果您想要處理前置字元。否則`FALSE`。  
  
 [in] `bRedraw`  
 `TRUE`如果您想要重繪索引標籤式的視窗。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 前置詞字元是助憶鍵字元前面加上連字號 （&）。  
  
##  <a name="a-namesetimagelista--cmfcbasetabctrlsetimagelist"></a><a name="setimagelist"></a>CMFCBaseTabCtrl::SetImageList  
 設定索引標籤控制項的圖示影像清單。  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx = 15,  
    COLORREF clrTransp = RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 點陣圖的資源 id。 `SetImageList`載入來自此資源的影像清單。  
  
 [in] `cx`  
 每個影像像素為單位的寬度。  
  
 [in] `clrTransp`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，表示影像的透明色彩。  
  
 [in] `hImageList`  
 預先載入的影像清單控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 索引標籤旁邊顯示圖示影像清單中的映像。 若要顯示圖示，您必須指定其索引當您呼叫[CMFCBaseTabCtrl::AddTab](#addtab)。  
  
 `SetImageList`如果建立索引標籤控制項的平面樣式，將會失敗。 它也會失敗如果架構無法載入所指示的映像`uiID`。  
  
 這個方法會重新計算 索引標籤，根據影像和文字大小的高度。  
  
##  <a name="a-namesetlocationa--cmfcbasetabctrlsetlocation"></a><a name="setlocation"></a>CMFCBaseTabCtrl::SetLocation  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetLocation(Location location);
```  
  
### <a name="parameters"></a>參數  
 [in] `location`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesettabbkcolora--cmfcbasetabctrlsettabbkcolor"></a><a name="settabbkcolor"></a>CMFCBaseTabCtrl::SetTabBkColor  
 設定指定的索引標籤的背景色彩。  
  
```  
virtual BOOL SetTabBkColor(
    int iTab,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
 [in] `color`  
 要設定的色彩。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FALSE`否則。  
  
##  <a name="a-namesettabbordersizea--cmfcbasetabctrlsettabbordersize"></a><a name="settabbordersize"></a>CMFCBaseTabCtrl::SetTabBorderSize  
 設定的新索引標籤控制項的框線大小。  
  
```  
virtual void SetTabBorderSize(
    int nTabBorderSize,  
    BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTabBorderSize`  
 新框線的大小，單位為像素。  
  
 [in] `bRepaint`  
 布林值的參數，指出架構是否重新繪製控制項。  
  
##  <a name="a-namesettabhicona--cmfcbasetabctrlsettabhicon"></a><a name="settabhicon"></a>CMFCBaseTabCtrl::SetTabHicon  
 設定索引標籤上標籤的圖示。  
  
```  
virtual BOOL SetTabHicon(
    int iTab,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。 這個方法會變更此索引標籤的圖示。  
  
 [in] `hIcon`  
 圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
##  <a name="a-namesettabicona--cmfcbasetabctrlsettabicon"></a><a name="settabicon"></a>CMFCBaseTabCtrl::SetTabIcon  
 設定索引標籤的圖示。  
  
```  
virtual BOOL SetTabIcon(
    int iTab,  
    UINT uiIcon);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 要更新之索引標籤以零為起始的索引。  
  
 [in] `uiIcon`  
 [新增] 圖示圖示識別碼。 此識別碼會參考內部[CImageList](../../mfc/reference/cimagelist-class.md)物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
##  <a name="a-namesettabicononlya--cmfcbasetabctrlsettabicononly"></a><a name="settabicononly"></a>CMFCBaseTabCtrl::SetTabIconOnly  
 啟用特定的索引標籤上顯示只有圖示 （和文字標籤）。  
  
```  
virtual BOOL SetTabIconOnly(
    int iTab,  
    BOOL bIconOnly = TRUE,  
    BOOL bShowTooltipAlways = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 若要變更索引標籤的以零起始的索引。  
  
 [in] `bIconOnly`  
 布林值的參數，決定是否要顯示只有圖示。  
  
 [in] `bShowTooltipAlways`  
 布林值的參數會決定是否架構顯示工具提示會顯示只有圖示的索引標籤標籤。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 根據預設，索引標籤控制項顯示每個索引標籤的圖示和文字標籤。  
  
##  <a name="a-namesettablabela--cmfcbasetabctrlsettablabel"></a><a name="settablabel"></a>CMFCBaseTabCtrl::SetTabLabel  
 設定索引標籤上標籤的文字。  
  
```  
virtual BOOL SetTabLabel(
    int iTab,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 要更新之索引標籤以零為起始的索引。  
  
 [in] `strLabel`  
 包含新索引標籤的標籤文字字串的參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
##  <a name="a-namesettabsheighta--cmfcbasetabctrlsettabsheight"></a><a name="settabsheight"></a>CMFCBaseTabCtrl::SetTabsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetTabsHeight();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesettabsordera--cmfcbasetabctrlsettabsorder"></a><a name="settabsorder"></a>CMFCBaseTabCtrl::SetTabsOrder  
 排列的索引標籤中指定的順序。  
  
```  
BOOL SetTabsOrder(const CArray<int,int>& arOrder);
```  
  
### <a name="parameters"></a>參數  
 [in] `arOrder`  
 定義新的 tab 鍵順序的以零為起始的索引陣列。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FAIL`否則。  
  
### <a name="remarks"></a>備註  
 大小`arOrder`陣列必須等於索引標籤控制項中的索引標籤數目。  
  
##  <a name="a-namesettabtextcolora--cmfcbasetabctrlsettabtextcolor"></a><a name="settabtextcolor"></a>CMFCBaseTabCtrl::SetTabTextColor  
 設定特定的索引標籤的文字色彩。  
  
```  
virtual BOOL SetTabTextColor(
    int iTab,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
 [in] `color`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數，指出新的文字色彩。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
##  <a name="a-nameshowtaba--cmfcbasetabctrlshowtab"></a><a name="showtab"></a>CMFCBaseTabCtrl::ShowTab  
 顯示或隱藏指定的索引標籤。  
  
```  
virtual BOOL ShowTab(
    int iTab,  
    BOOL bShow = TRUE,  
    BOOL bRecalcLayout = TRUE,  
    BOOL bActivate = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的索引，`ShowTab`會顯示或隱藏。  
  
 [in] `bShow`  
 布林值的參數，指出是否顯示索引標籤。  
  
 [in] `bRecalcLayout`  
 布林值的參數，指出是否要立即重新計算的視窗配置。  
  
 [in] `bActivate`  
 布林值參數，指出是否要選取所指定的索引標籤`iTab`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 參數`bActivate`才會套用`bShow`是`TRUE`。 如果`bActivate`是`TRUE`如果`ShowTab`成功，`ShowTab`會將訊息 AFX_WM_CHANGE_ACTIVE_TAB 傳送 索引標籤視窗的父代。  
  
##  <a name="a-namestartrenametaba--cmfcbasetabctrlstartrenametab"></a><a name="startrenametab"></a>CMFCBaseTabCtrl::StartRenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL StartRenameTab(int iTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameswaptabsa--cmfcbasetabctrlswaptabs"></a><a name="swaptabs"></a>CMFCBaseTabCtrl::SwapTabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SwapTabs(
    int nFisrtTabID,  
    int nSecondTabID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nFisrtTabID`  
 [in] `nSecondTabID`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl 類別](../../mfc/reference/cmfctabctrl-class.md)   
 [CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

