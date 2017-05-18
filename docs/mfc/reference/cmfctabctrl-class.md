---
title: "CMFCTabCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl::ActivateMDITab
- AFXTABCTRL/CMFCTabCtrl::AllowDestroyEmptyTabbedPane
- AFXTABCTRL/CMFCTabCtrl::AutoSizeWindow
- AFXTABCTRL/CMFCTabCtrl::CalcRectEdit
- AFXTABCTRL/CMFCTabCtrl::Create
- AFXTABCTRL/CMFCTabCtrl::EnableActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::EnableInPlaceEdit
- AFXTABCTRL/CMFCTabCtrl::EnableTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::EnsureVisible
- AFXTABCTRL/CMFCTabCtrl::GetDocumentIcon
- AFXTABCTRL/CMFCTabCtrl::GetFirstVisibleTabNum
- AFXTABCTRL/CMFCTabCtrl::GetResizeMode
- AFXTABCTRL/CMFCTabCtrl::GetScrollBar
- AFXTABCTRL/CMFCTabCtrl::GetTabArea
- AFXTABCTRL/CMFCTabCtrl::GetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::GetTabsHeight
- AFXTABCTRL/CMFCTabCtrl::GetTabsRect
- AFXTABCTRL/CMFCTabCtrl::GetWndArea
- AFXTABCTRL/CMFCTabCtrl::HideActiveWindowHorzScrollBar
- AFXTABCTRL/CMFCTabCtrl::HideInactiveWindow
- AFXTABCTRL/CMFCTabCtrl::HideNoTabs
- AFXTABCTRL/CMFCTabCtrl::HideSingleTab
- AFXTABCTRL/CMFCTabCtrl::IsActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::IsDrawFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatTab
- AFXTABCTRL/CMFCTabCtrl::IsLeftRightRounded
- AFXTABCTRL/CMFCTabCtrl::IsMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsOneNoteStyle
- AFXTABCTRL/CMFCTabCtrl::IsSharedScroll
- AFXTABCTRL/CMFCTabCtrl::IsTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::IsVS2005Style
- AFXTABCTRL/CMFCTabCtrl::ModifyTabStyle
- AFXTABCTRL/CMFCTabCtrl::OnDragEnter
- AFXTABCTRL/CMFCTabCtrl::OnDragOver
- AFXTABCTRL/CMFCTabCtrl::OnShowTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::SetActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::SetActiveTab
- AFXTABCTRL/CMFCTabCtrl::SetActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::SetDrawFrame
- AFXTABCTRL/CMFCTabCtrl::SetFlatFrame
- AFXTABCTRL/CMFCTabCtrl::SetImageList
- AFXTABCTRL/CMFCTabCtrl::SetResizeMode
- AFXTABCTRL/CMFCTabCtrl::SetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::StopResize
- AFXTABCTRL/CMFCTabCtrl::SynchronizeScrollBar
- AFXTABCTRL/CMFCTabCtrl::m_bEnableActivate
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabCtrl::SwapTabs method
- CMFCTabCtrl constructor
- CMFCTabCtrl::MoveTab method
- CMFCTabCtrl::GetTabFromPoint method
- CMFCTabCtrl::PreTranslateMessage method
- CMFCTabCtrl::RecalcLayout method
- CMFCTabCtrl class
- CMFCTabCtrl::IsPtInTabArea method
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
caps.latest.revision: 33
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 595ff7fbcd55f3b756ce650e02b6247b898d7629
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctabctrl-class"></a>CMFCTabCtrl Class
`CMFCTabCtrl`類別會提供索引標籤控制項的功能。 索引標籤控制項會顯示頂端或底部有一般或&3;D 索引標籤的可停駐視窗。 索引標籤可以顯示文字和影像，當在使用中狀態時，也可變更色彩。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCTabCtrl::CMFCTabCtrl`|預設建構函式。|  
|`CMFCTabCtrl::~CMFCTabCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCTabCtrl::ActivateMDITab](#activatemditab)|顯示目前的索引標籤控制項的指定索引標籤，並將焦點設在該索引標籤。|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)||  
|[CMFCTabCtrl::AutoSizeWindow](#autosizewindow)|指定是否要調整大小的所有索引標籤上控制 windows 使用者介面項目 索引標籤的控制項變更時的工作區架構。|  
|[CMFCTabCtrl::CalcRectEdit](#calcrectedit)|「 洩氣 」 指定的索引標籤區域的大小。 (覆寫 `CMFCBaseTabCtrl::CalcRectEdit`。)|  
|[CMFCTabCtrl::Create](#create)|建立索引標籤控制項並將它附加`CMFCTabCtrl`物件。|  
|`CMFCTabCtrl::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](#enableactivetabclosebutton)|顯示或隱藏 關閉 按鈕 ( **X**) 在使用中 索引標籤。|  
|[CMFCTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|啟用或停用可編輯的索引標籤。 (覆寫[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)。)|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)|取代捲動按鈕可開啟功能表的 索引標籤式視窗的視窗索引標籤的兩個按鈕。|  
|[CMFCTabCtrl::EnsureVisible](#ensurevisible)|請確定索引標籤會出現。|  
|[CMFCTabCtrl::GetDocumentIcon](#getdocumenticon)|擷取與索引標籤式視窗的快顯功能表中的索引標籤相關聯的符號。|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)|擷取會在目前的索引標籤控制項中顯示的第一個索引標籤的索引。|  
|[CMFCTabCtrl::GetResizeMode](#getresizemode)|擷取值，指定如何在目前的索引標籤控制項可以調整大小。|  
|[CMFCTabCtrl::GetScrollBar](#getscrollbar)|擷取與索引標籤控制項相關聯的捲軸列物件的指標。|  
|[CMFCTabCtrl::GetTabArea](#gettabarea)|擷取的頂端或底部的索引標籤控制項 索引標籤標籤區域的周框矩形。 (覆寫[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)。)|  
|`CMFCTabCtrl::GetTabFromPoint`|擷取包含指定的點的索引標籤。 (覆寫[CMFCBaseTabCtrl::GetTabFromPoint](../../mfc/reference/cmfcbasetabctrl-class.md#gettabfrompoint)。)|  
|[CMFCTabCtrl::GetTabMaxWidth](#gettabmaxwidth)|擷取索引標籤的最大寬度。|  
|[CMFCTabCtrl::GetTabsHeight](#gettabsheight)|擷取目前的索引標籤控制項的索引標籤區域的高度。|  
|[CMFCTabCtrl::GetTabsRect](#gettabsrect)|擷取限定在目前的索引標籤控制項的索引標籤區域的矩形的。 (覆寫[CMFCBaseTabCtrl::GetTabsRect](../../mfc/reference/cmfcbasetabctrl-class.md#gettabsrect)。)|  
|`CMFCTabCtrl::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCTabCtrl::GetWndArea](#getwndarea)|擷取目前的索引標籤控制項的用戶端區域的界限。|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)|如果有使用中視窗的，隱藏水平捲軸列。|  
|[CMFCTabCtrl::HideInactiveWindow](#hideinactivewindow)|指定是否要顯示非作用中 索引標籤控制項的 windows 架構。|  
|[CMFCTabCtrl::HideNoTabs](#hidenotabs)|啟用或停用 [繪圖] 索引標籤區域，如果不有任何可見的索引標籤。|  
|[CMFCTabCtrl::HideSingleTab](#hidesingletab)|啟用或停用單一索引標籤式的視窗時，繪製一個索引標籤。 (覆寫[CMFCBaseTabCtrl::HideSingleTab](../../mfc/reference/cmfcbasetabctrl-class.md#hidesingletab)。)|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](#isactiveinmditabgroup)|指出目前的索引標籤的索引標籤控制項是否為多個文件介面 索引標籤群組中的 作用中 索引標籤。|  
|[CMFCTabCtrl::IsActiveTabBoldFont](#isactivetabboldfont)|指出是否使用中 索引標籤的文字會顯示使用粗體字型。|  
|[CMFCTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)|指出是否 [關閉] 按鈕 ( **X**) 會顯示在作用中的索引標籤或索引標籤區域右上角。|  
|[CMFCTabCtrl::IsDrawFrame](#isdrawframe)|指出是否索引標籤式的視窗框架周圍繪製矩形內嵌的窗格。|  
|[CMFCTabCtrl::IsFlatFrame](#isflatframe)|指出是否平面或 3D 索引標籤區域外的框。|  
|[CMFCTabCtrl::IsFlatTab](#isflattab)|指出是否一般或不在目前的索引標籤控制項索引標籤的外觀。|  
|[CMFCTabCtrl::IsLeftRightRounded](#isleftrightrounded)|指出是否要四捨五入的左側和右側，目前的索引標籤控制項中的索引標籤的外觀。|  
|[CMFCTabCtrl::IsMDITabGroup](#ismditabgroup)|指出目前的索引標籤控制項是否包含多個文件介面視窗的工作區中。|  
|[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)|指出是否要將目前的索引標籤控制項顯示 Microsoft onenote 樣式。|  
|`CMFCTabCtrl::IsPtInTabArea`|決定在索引標籤區域內時點。 (覆寫[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)。)|  
|[CMFCTabCtrl::IsSharedScroll](#issharedscroll)|指出目前的索引標籤控制項是否已捲軸可以捲動其 索引標籤，為群組。|  
|[CMFCTabCtrl::IsTabDocumentsMenu](#istabdocumentsmenu)|表示索引標籤控制項是否顯示捲軸按鈕或按鈕，可顯示索引標籤式視窗的功能表。|  
|[CMFCTabCtrl::IsVS2005Style](#isvs2005style)|指出是否顯示索引標籤，以在 Visual Studio.NET 2005年樣式。|  
|[CMFCTabCtrl::ModifyTabStyle](#modifytabstyle)|指定目前的索引標籤控制項中的索引標籤的外觀。|  
|`CMFCTabCtrl::MoveTab`|將索引標籤移到另一個索引標籤的位置。 (覆寫[CMFCBaseTabCtrl::MoveTab](../../mfc/reference/cmfcbasetabctrl-class.md#movetab)。)|  
|[CMFCTabCtrl::OnDragEnter](#ondragenter)|資料指標第一次拖曳至 [索引標籤控制項] 視窗時，由架構呼叫。|  
|[CMFCTabCtrl::OnDragOver](#ondragover)|當滑鼠移動經過置放目標視窗呼叫由架構在拖曳作業期間。 (覆寫[CMFCBaseTabCtrl::OnDragOver](../../mfc/reference/cmfcbasetabctrl-class.md#ondragover)。)|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](#onshowtabdocumentsmenu)|顯示索引標籤式視窗的快顯功能表中，會等到使用者選取索引標籤，並將選取的索引標籤為作用中索引標籤。|  
|`CMFCTabCtrl::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CMFCBaseTabCtrl::PreTranslateMessage](../../mfc/reference/cmfcbasetabctrl-class.md#pretranslatemessage)。)|  
|`CMFCTabCtrl::RecalcLayout`|重新計算索引標籤控制項的內部配置。 (覆寫[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)。)|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](#setactiveinmditabgroup)|將索引標籤控制項的 [目前] 索引標籤設為作用中的索引標籤，在多個文件介面索引標籤群組。|  
|[CMFCTabCtrl::SetActiveTab](#setactivetab)|啟動索引標籤。 (覆寫[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)。)|  
|[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)|啟用或停用使用的作用中 索引標籤上的粗體字型。|  
|[CMFCTabCtrl::SetDrawFrame](#setdrawframe)|啟用或停用內嵌的列 drawinga 框矩形。|  
|[CMFCTabCtrl::SetFlatFrame](#setflatframe)|指定是否要繪製以平面或 3D 框架 索引標籤區域。|  
|[CMFCTabCtrl::SetImageList](#setimagelist)|指定映像清單。 (覆寫[CMFCBaseTabCtrl::SetImageList](../../mfc/reference/cmfcbasetabctrl-class.md#setimagelist)。)|  
|[CMFCTabCtrl::SetResizeMode](#setresizemode)|指定如何在目前的索引標籤控制項可以調整大小，然後重新顯示控制項。|  
|[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)|指定在索引標籤式視窗的最大值 索引標籤寬度。|  
|[CMFCTabCtrl::StopResize](#stopresize)|終止目前的調整大小作業 索引標籤控制項上。|  
|`CMFCTabCtrl::SwapTabs`|交換一組索引標籤。 (覆寫[CMFCBaseTabCtrl::SwapTabs](../../mfc/reference/cmfcbasetabctrl-class.md#swaptabs)。)|  
|[CMFCTabCtrl::SynchronizeScrollBar](#synchronizescrollbar)|一般索引標籤會顯示在索引標籤控制項上繪製水平捲軸。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCTabCtrl::m_bEnableActivate](#m_benableactivate)|防止使用中的檢視是插入新的索引標籤，並啟用時，失去焦點。|  
  
## <a name="remarks"></a>備註  
 `CMFCTabCtrl`類別支援︰  
  
-   包含 3D，一般模式，以及一般共用水平捲軸的控制項樣式 索引標籤。  
  
-   位於上方或下方的視窗 索引標籤。  
  
-   顯示文字、 影像或文字及影像的索引標籤。  
  
-   使用中 索引標籤時，變更色彩的索引標籤。  
  
-   調整索引標籤的框線大小變更。  
  
-   可拆式索引標籤式的視窗。  
  
 `CMFCTabCtrl`類別可以使用對話方塊中，但適用於應用程式使用停駐控制列，例如[!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)]和[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。 如需詳細資訊，請參閱[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)。  
  
 請遵循下列步驟來新增可調整停駐在應用程式中的索引標籤控制項︰  
  
1.  建立的執行個體[CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)。  
  
2.  呼叫[CDockablePane::Create](../../mfc/reference/cdockablepane-class.md#create)。  
  
3.  使用[CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab)或[CMFCBaseTabCtrl::InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)加入新的索引標籤。  
  
4.  呼叫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking) ，讓目前的停駐 索引標籤控制項可以停駐於主框架視窗。  
  
5.  呼叫[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)停駐於主框架的索引標籤式的視窗。  
  
 如需如何建立為停駐控制列的索引標籤式的視窗的範例，請參閱[CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)。 若要使用`CMFCTabCtrl`做為非停駐的控制項，建立`CMFCTabCtrl`物件，然後呼叫[CMFCTabCtrl::Create](#create)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCTabCtrl`類別來設定`CMFCTabCtrl`物件。 此範例說明如何加入索引標籤，顯示作用中 索引標籤上的 關閉 按鈕，啟用可編輯的索引標籤，並顯示索引標籤式的視窗標籤快顯功能表。 這個範例是屬於[狀態集合範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection #&1;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection #&3;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtabctrl.h  
  
##  <a name="activatemditab"></a>CMFCTabCtrl::ActivateMDITab  
 顯示目前的索引標籤控制項的指定索引標籤，並將焦點設在該索引標籤。  
  
```  
void ActivateMDITab(int nTab = -1);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTab`  
 索引標籤以顯示，或是-1，指定目前使用中 索引標籤以零為起始的索引。  
  
##  <a name="allowdestroyemptytabbedpane"></a>CMFCTabCtrl::AllowDestroyEmptyTabbedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="autosizewindow"></a>CMFCTabCtrl::AutoSizeWindow  
 指定是否要調整大小的所有索引標籤上控制 windows 使用者介面項目 索引標籤的控制項變更時的工作區架構。  
  
```  
void AutoSizeWindow(BOOL bAutoSize = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAutoSize`  
 `TRUE`自動調整 索引標籤控制項視窗中︰否則， `FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="create"></a>CMFCTabCtrl::Create  
 建立索引標籤控制項並將它附加`CMFCTabCtrl`物件。  
  
```  
BOOL Create(
    Style style,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    Location location=LOCATION_BOTTOM,  
    BOOL bCloseBtn=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `style`  
 索引標籤控制項的樣式。 如需詳細資訊，請參閱＜備註＞。  
  
 [in] `rect`  
 矩形的索引標籤控制項 （繫結）。  
  
 [in] `pParentWnd`  
 父視窗的指標。 必須不是 `NULL`。  
  
 [in] `nID`  
 索引標籤控制項的 ID。  
  
 [in] `location`  
 索引標籤的位置。 預設值是 `LOCATION_BOTTOM`。 如需詳細資訊，請參閱＜備註＞。  
  
 [in] `bCloseBtn`  
 `TRUE`若要顯示 關閉 按鈕 索引標籤上，否則， `FALSE`。 預設值是 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 如果成功即為 `TRUE`；否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
 下表描述您可以針對指定的值`style`參數。  
  
|樣式|描述|  
|-----------|-----------------|  
|STYLE_3D|建立有立體外觀的索引標籤控制項。|  
|STYLE_FLAT|一般索引標籤建立索引標籤控制項。|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|建立具有一般索引標籤和捲軸可以捲動索引標籤，如果父視窗裁剪 索引標籤控制項。|  
|STYLE_3D_ONENOTE|Microsoft onenote 樣式建立的索引標籤控制項。|  
|STYLE_3D_VS2005|建立索引標籤控制項中的 Microsoft Visual Studio 2005 的樣式。|  
|STYLE_3D_ROUNDED|建立具有圓角的索引標籤中的 Microsoft Visual Studio 2005 樣式 索引標籤控制項。|  
|STYLE_3D_ROUNDED_SCROLL|建立具有圓角的索引標籤和 Microsoft Visual Studio 2005 的樣式中的捲軸按鈕 索引標籤控制項。|  
  
 下表列出您可以針對指定的值`location`參數。  
  
|位置|描述|  
|--------------|-----------------|  
|LOCATION_BOTTOM|索引標籤位於底部的索引標籤控制項。|  
|LOCATION_TOP|索引標籤位於頂端的索引標籤控制項。|  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法中的`CMFCTabCtrl`類別。 這個範例是屬於[狀態集合範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection #&1;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection #&2;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_3.cpp)]  
  
##  <a name="calcrectedit"></a>CMFCTabCtrl::CalcRectEdit  
 「 洩氣 」 指定的索引標籤區域的大小。  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>參數  
 [in] `rectEdit`  
 指定的索引標籤區域的矩形。  
  
### <a name="remarks"></a>備註  
 當您變更索引標籤的標籤時，會呼叫這個方法。 這個方法 deflate 左側與右側相加，指定矩形的一半目前的索引標籤高度，並 「 洩氣 」 上、 下一個單位。  
  
##  <a name="enableactivetabclosebutton"></a>CMFCTabCtrl::EnableActiveTabCloseButton  
 顯示或隱藏 關閉 按鈕 ( **X**) 在使用中 索引標籤。  
  
```  
void EnableActiveTabCloseButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要在作用中 索引標籤，顯示 關閉 按鈕`FALSE`以顯示索引標籤區域右上角的 關閉 按鈕。 預設值是 `TRUE`。  
  
##  <a name="enableinplaceedit"></a>CMFCTabCtrl::EnableInPlaceEdit  
 啟用或停用可編輯的索引標籤。  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用可編輯的索引標籤。`FALSE`停用可編輯的索引標籤。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enabletabdocumentsmenu"></a>CMFCTabCtrl::EnableTabDocumentsMenu  
 使用兩個按鈕捲動視窗索引標籤的使用者介面與介面，以顯示快顯功能表的 索引標籤式視窗之間切換。  
  
```  
void EnableTabDocumentsMenu(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要顯示的快顯功能表索引標籤式視窗的標籤。`FALSE`向前及向後捲動按鈕顯示。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 當使用者按一下索引標籤的標籤時，架構會顯示對應的索引標籤式的視窗。 如果 索引標籤的標籤為可見，而不需要變更它的位置開啟索引標籤式的視窗。 如果使用者從快顯功能表選取 文件對應的索引標籤式的視窗已關閉螢幕，索引標籤式的視窗就會成為第一個索引標籤。  
  
##  <a name="ensurevisible"></a>CMFCTabCtrl::EnsureVisible  
 請確定索引標籤會出現。  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。`FALSE`如果`iTab`參數索引無效。  
  
### <a name="remarks"></a>備註  
 使用這個方法，以確保指定的索引標籤是可見。 如果需要，將捲動索引標籤控制項。  
  
##  <a name="getdocumenticon"></a>CMFCTabCtrl::GetDocumentIcon  
 擷取與索引標籤式視窗的快顯功能表中的索引標籤相關聯的映像。  
  
```  
static HICON __stdcall GetDocumentIcon(UINT nCmdID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nCmdID`  
 命令 ID 的索引標籤式視窗的快顯功能表中的索引標籤。  
  
### <a name="return-value"></a>傳回值  
 點陣圖影像的控制代碼。  
  
##  <a name="getfirstvisibletabnum"></a>CMFCTabCtrl::GetFirstVisibleTabNum  
 擷取會在目前的索引標籤控制項中顯示的第一個索引標籤的索引。  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤控制項中的索引標籤以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 Microsoft onenote 的樣式會顯示索引標籤控制項時，才使用這個方法。 使用[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)方法，以判斷樣式。  
  
##  <a name="getresizemode"></a>CMFCTabCtrl::GetResizeMode  
 擷取值，指定如何在目前的索引標籤控制項可以調整大小。  
  
```  
ResizeMode GetResizeMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 其中一個`CMFCTabCtrl::ResizeMode`列舉值，指定可調整大小的索引標籤控制項的方式。 如需可能值的清單，請參閱的 < 備註 > 一節[CMFCTabCtrl::SetResizeMode](#setresizemode)方法。  
  
##  <a name="getscrollbar"></a>CMFCTabCtrl::GetScrollBar  
 擷取與索引標籤控制項相關聯的捲軸列物件的指標。  
  
```  
CScrollBar* GetScrollBar();
```  
  
### <a name="return-value"></a>傳回值  
 捲軸物件、 指標或`NULL`若未建立索引標籤控制項使用`STYLE_FLAT_SHARED_HORZ_SCROLL`樣式。  
  
### <a name="remarks"></a>備註  
 使用這個方法來存取索引標籤控制項的內嵌的捲軸。 捲軸列物件會建立具有索引標籤控制項時，才`STYLE_FLAT_SHARED_HORZ_SCROLL`樣式。  
  
##  <a name="gettabarea"></a>CMFCTabCtrl::GetTabArea  
 擷取的頂端或底部的索引標籤控制項 索引標籤標籤區域的周框矩形。  
  
```  
void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectTabAreaTop`  
 此方法傳回時，此參考會包含限定上方的索引標籤的標籤區域的矩形。 矩形是在工作區座標。 此參考是空白，如果沒有索引標籤的標籤區域頂端的索引標籤控制項。  
  
 [輸出] `rectTabAreaBottom`  
 此方法傳回時，此參考會包含限定底部 索引標籤的標籤區域的矩形的。 矩形是在工作區座標。 此參考是空白，如果沒有索引標籤的標籤區域底部的索引標籤控制項。  
  
### <a name="remarks"></a>備註  
 使用這個方法來決定的大小和索引標籤式視窗中的索引標籤區域位置。  
  
##  <a name="gettabmaxwidth"></a>CMFCTabCtrl::GetTabMaxWidth  
 擷取索引標籤的最大寬度。  
  
```  
int GetTabMaxWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤上，單位為像素的最大寬度。 如果傳回值為 0，索引標籤寬度沒有限制。  
  
### <a name="remarks"></a>備註  
 使用[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)方法來設定最大值 索引標籤的寬度。  
  
##  <a name="gettabsheight"></a>CMFCTabCtrl::GetTabsHeight  
 擷取目前的索引標籤控制項的索引標籤區域的高度。  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果任何索引標籤是可見的或如果沒有索引標籤會顯示索引標籤區域的高度。  
  
##  <a name="gettabsrect"></a>CMFCTabCtrl::GetTabsRect  
 擷取限定在目前的索引標籤控制項的索引標籤區域的矩形的。  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rect`  
 此方法傳回時，`rect`參數會包含限定 索引標籤區域的矩形。  
  
##  <a name="getwndarea"></a>CMFCTabCtrl::GetWndArea  
 擷取目前的索引標籤控制項的用戶端區域的界限。  
  
```  
void GetWndArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
 [in、out] `rect`  
 此方法傳回時，此參數會包含目前的索引標籤控制項 （繫結） 的矩形。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hideactivewindowhorzscrollbar"></a>CMFCTabCtrl::HideActiveWindowHorzScrollBar  
 水平捲軸中，如果隱藏任何使用中視窗。  
  
```  
void HideActiveWindowHorzScrollBar();
```  
  
### <a name="remarks"></a>備註  
 若要防止索引標籤控制項閃爍的使用者 索引標籤控制項頁面之間切換時，使用這個方法。  
  
##  <a name="hideinactivewindow"></a>CMFCTabCtrl::HideInactiveWindow  
 指定是否，架構會顯示非作用中 索引標籤控制項的視窗。  
  
```  
void HideInactiveWindow(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHide`  
 `TRUE`不想再顯示非作用中的視窗。`FALSE`顯示非作用中的視窗。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hidenotabs"></a>CMFCTabCtrl::HideNoTabs  
 啟用或停用的索引標籤區域繪圖，如果不有任何可見的索引標籤。  
  
```  
void HideNoTabs(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHide`  
 `TRUE`若要啟用 [繪圖] 索引標籤區域中。`FALSE`停用繪製。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="hidesingletab"></a>CMFCTabCtrl::HideSingleTab  
 啟用或停用索引標籤的繪製，如果沒有單一的索引標籤式的視窗。  
  
```  
virtual void HideSingleTab(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bHide`  
 `TRUE`不繪製單一索引標籤式視窗; 的索引標籤`FALSE`繪製單一索引標籤。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isactiveinmditabgroup"></a>CMFCTabCtrl::IsActiveInMDITabGroup  
 指出目前的索引標籤的索引標籤控制項是否為多個文件介面 索引標籤群組中的 作用中 索引標籤。  
  
```  
BOOL IsActiveInMDITabGroup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果目前的索引標籤索引標籤控制項的作用中的索引標籤中 MDI 索引標籤群組。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以將多個文件視窗組織成任一個垂直或水平索引標籤群組，並輕鬆地從一個索引標籤群組到另一個隨機文件。  
  
##  <a name="isactivetabboldfont"></a>CMFCTabCtrl::IsActiveTabBoldFont  
 指出是否使用中 索引標籤的文字會顯示使用粗體字型。  
  
```  
BOOL IsActiveTabBoldFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果使用中的索引標籤會顯示使用粗體字型。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)方法，以變更作用中索引標籤的字型。  
  
##  <a name="isactivetabclosebutton"></a>CMFCTabCtrl::IsActiveTabCloseButton  
 指出是否 [關閉] 按鈕 ( **X**) 會顯示在作用中的索引標籤上，或索引標籤區域右上角。  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 關閉 按鈕會顯示在作用中的索引標籤。`FALSE`如果 索引標籤區域右上角顯示 關閉 按鈕。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isdrawframe"></a>CMFCTabCtrl::IsDrawFrame  
 指出是否索引標籤式的視窗框架周圍繪製矩形內嵌的窗格。  
  
```  
BOOL IsDrawFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果框架繪製矩形。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CMFCTabCtrl::SetDrawFrame](#setdrawframe)方法，以啟用或停用繪製框矩形。  
  
##  <a name="isflatframe"></a>CMFCTabCtrl::IsFlatFrame  
 指出是否平面或 3D 索引標籤區域外的框。  
  
```  
BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤區域周圍框架的一般;`FALSE`如果框架為&3;d。  
  
### <a name="remarks"></a>備註  
 使用[CMFCTabCtrl::SetFlatFrame](#setflatframe)方法，以變更繪製框架的方式。  
  
##  <a name="isflattab"></a>CMFCTabCtrl::IsFlatTab  
 指出是否一般或不在目前的索引標籤控制項索引標籤的外觀。  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果目前的索引標籤控制項中的索引標籤的外觀是一般。否則， `FALSE`。  
  
##  <a name="isleftrightrounded"></a>CMFCTabCtrl::IsLeftRightRounded  
 指出是否要四捨五入的左側和右側，目前的索引標籤控制項中的索引標籤的外觀。  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果會捨入的每個索引標籤旁邊。，否則， `FALSE`。  
  
##  <a name="ismditabgroup"></a>CMFCTabCtrl::IsMDITabGroup  
 指出目前的索引標籤控制項是否包含多個文件介面視窗的工作區中。  
  
```  
virtual BOOL IsMDITabGroup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果目前的索引標籤控制項是在 MDI 工作區視窗;否則， `FALSE`。  
  
##  <a name="isonenotestyle"></a>CMFCTabCtrl::IsOneNoteStyle  
 指出是否要將目前的索引標籤控制項顯示 Microsoft onenote 樣式。  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 Microsoft onenote; 樣式中顯示索引標籤控制項否則， `FALSE`。  
  
##  <a name="issharedscroll"></a>CMFCTabCtrl::IsSharedScroll  
 指出目前的索引標籤控制項是否已捲軸可以捲動其 索引標籤，為群組。  
  
```  
BOOL IsSharedScroll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤控制項有共用的捲軸。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`TRUE`如果`style`參數[CMFCTabCtrl::Create](#create)方法是 STYLE_FLAT_SHARED_HORZ_SCROLL。  
  
##  <a name="istabdocumentsmenu"></a>CMFCTabCtrl::IsTabDocumentsMenu  
 表示索引標籤控制項是否顯示捲軸按鈕或按鈕，可顯示索引標籤式視窗的功能表。  
  
```  
BOOL IsTabDocumentsMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤式的視窗將捲動使用快顯功能表的索引標籤式的視窗的標籤。`FALSE`如果索引標籤式的視窗將捲動使用向前及向後捲動按鈕。  
  
### <a name="remarks"></a>備註  
 使用[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)方法，以指定的方法捲動的索引視窗。  
  
##  <a name="isvs2005style"></a>CMFCTabCtrl::IsVS2005Style  
 指出是否索引標籤的繪製使用 Visual Studio 2005 的樣式。  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤的繪製樣式的 Visual Studio 2005;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用`style`參數[CMFCTabCtrl::Create](#create)方法，以指定索引標籤的繪製方式。  
  
##  <a name="m_benableactivate"></a>CMFCTabCtrl::m_bEnableActivate  
 防止使用中的檢視是插入新的索引標籤，並啟用時，失去焦點。  
  
```  
static BOOL m_bEnableActivate;  
```  
  
### <a name="remarks"></a>備註  
 當 [] 索引標籤插入，並且成為使用中新的索引標籤式視窗通常是採取焦點。 設定`CMFCTabCtrl::m_bEnableActivate`成員變數來`FALSE`保留原始的焦點。 預設值是 `TRUE`。  
  
##  <a name="modifytabstyle"></a>CMFCTabCtrl::ModifyTabStyle  
 指定目前的索引標籤控制項中的索引標籤的外觀。  
  
```  
BOOL ModifyTabStyle(Style style);
```  
  
### <a name="parameters"></a>參數  
 [in] `style`  
 其中一個列舉值，指定索引標籤控制項的外觀。 如需詳細資訊，請參閱 < 備註 > 中的資料表。  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 值`style`參數可以是下列其中一種`CMFCTabCtrl::Style`列舉型別。  
  
|名稱|描述|  
|----------|-----------------|  
|STYLE_3D|顯示&3;d、 矩形有圓角的索引標籤。|  
|STYLE_3D_ONENOTE|顯示&3;d 索引標籤具有垂直一邊與斜體的一端，而且，具有圓角。|  
|STYLE_3D_ROUNDED|顯示具有傾斜側邊和圓角的三維索引標籤。|  
|STYLE_3D_ROUNDED_SCROLL|顯示具有傾斜側邊和圓角的三維索引標籤。 如果有多個索引標籤可以顯示在相同的時間比，架構會顯示下拉箭號和定位點以使用中的功能表。|  
|STYLE_3D_SCROLLED|顯示&3;d、 矩形的索引標籤。 如果有多個索引標籤可以顯示在相同的時間比，架構會顯示下拉箭號和定位點以使用中的功能表。|  
|STYLE_3D_VS2005|顯示&3;d，捨入有一端斜體和一個垂直邊的索引標籤。|  
|STYLE_FLAT|顯示具有傾斜左邊和右邊的二維索引標籤。|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|顯示二維索引標籤。 如果有多個索引標籤可以顯示在相同的時間比，，架構會顯示端點索引標籤區域的捲動箭號。|  
  
##  <a name="ondragenter"></a>CMFCTabCtrl::OnDragEnter  
 資料指標第一次進入目前的索引標籤控制項的視窗時呼叫 framework 拖放作業期間。  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDataObject`  
 資料物件，其中包含使用者拖曳的資料點。  
  
 [in] `dwKeyState`  
 包含輔助按鍵的狀態。 這是參數的位元組合 (OR) 的下列值︰ `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。 如需詳細資訊，請參閱**訊息參數**區段[有關滑鼠輸入](http://msdn.microsoft.com/library/windows/desktop/ms645601)。  
  
 [in] `point`  
 包含用戶端座標中的資料指標目前位置。  
  
### <a name="return-value"></a>傳回值  
 一律`DROPEFFECT_NONE`，這表示置放目標無法接受資料。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法支援拖放作業。 覆寫這個方法，以實作您自己的自訂行為。  
  
 根據預設，這個方法只會呼叫`CMFCTabCtrl::OnDragOver`，它一定會傳回`DROPEFFECT_NONE`。  
  
##  <a name="ondragover"></a>CMFCTabCtrl::OnDragOver  
 當滑鼠移動經過置放目標視窗呼叫由架構在拖曳作業期間。  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDataObject`  
 指標[COleDataObject](../../mfc/reference/coledataobject-class.md)拖曳到置放目標物件。  
  
 [in] `dwKeyState`  
 輔助按鍵的位元組合 （或者） 的狀態`MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。 如需詳細資訊，請參閱 < 訊息參數 」[有關滑鼠輸入](http://msdn.microsoft.com/library/windows/desktop/ms645601)。  
  
 [in] `point`  
 目前的滑鼠位置。  
  
### <a name="return-value"></a>傳回值  
 一定是 `DROPEFFECT_NONE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您的自訂實作。 如需詳細資訊，請參閱[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)方法。  
  
##  <a name="onshowtabdocumentsmenu"></a>CMFCTabCtrl::OnShowTabDocumentsMenu  
 顯示索引標籤式視窗的快顯功能表中，會等到使用者選取索引標籤，並將選取的索引標籤為作用中索引標籤。  
  
```  
virtual void OnShowTabDocumentsMenu(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 顯示快顯功能表上的位置座標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setactiveinmditabgroup"></a>CMFCTabCtrl::SetActiveInMDITabGroup  
 將索引標籤控制項的 目前 索引標籤設為多個文件介面 索引標籤群組中的 作用中 索引標籤。  
  
```  
void SetActiveInMDITabGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActive`  
 `TRUE`讓目前的索引標籤作用中的索引標籤。`FALSE`來停用目前的索引標籤。  
  
### <a name="remarks"></a>備註  
 您可以將多個文件視窗組織成任一個垂直或水平索引標籤群組，並輕鬆地從一個索引標籤群組到另一個隨機文件。  
  
##  <a name="setactivetab"></a>CMFCTabCtrl::SetActiveTab  
 啟動索引標籤。  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTab`  
 指定啟動 索引標籤的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的索引標籤已啟用。`FALSE`如果指定`iTab`參數值無效。  
  
### <a name="remarks"></a>備註  
 這個方法不會傳送`AFX_WM_CHANGE_ACTIVE_TAB`通知給父視窗的索引標籤控制項。  
  
 `SetActiveTab`方法會自動呼叫[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)方法，以避免使螢幕閃爍。  
  
##  <a name="setactivetabboldfont"></a>CMFCTabCtrl::SetActiveTabBoldFont  
 啟用或停用使用的作用中 索引標籤上的粗體字型。  
  
```  
void SetActiveTabBoldFont(BOOL bIsBold=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsBold`  
 `TRUE`使用以粗體字顯示標籤的 [作用中] 索引標籤。`FALSE`使用標準的字型來顯示標籤。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setdrawframe"></a>CMFCTabCtrl::SetDrawFrame  
 指定是否框架周圍繪製矩形內嵌的列。  
  
```  
void SetDrawFrame(BOOL bDraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDraw`  
 `TRUE`若要顯示框架矩形以圍繞內嵌的列。否則， `FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setflatframe"></a>CMFCTabCtrl::SetFlatFrame  
 指定是否要繪製以平面或 3D 框架 索引標籤區域。  
  
```  
void SetFlatFrame(
    BOOL bFlat=TRUE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bFlat`  
 `TRUE`要繪製 (2D) 平面框架 索引標籤區域中。`FALSE`繪製三維 (3D) 框架。 預設值是 `TRUE`。  
  
 [in] `bRepaint`  
 `TRUE`若要立即; 重繪視窗否則， `FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setimagelist"></a>CMFCTabCtrl::SetImageList  
 指定映像清單。  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx=15,  
    COLORREF clrTransp=RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
 包含影像清單的點陣圖資源識別碼。  
  
 [in] `cx`  
 每個映像，單位為像素的寬度。 預設值為 15。  
  
 [in] `clrTransp`  
 透明影像的色彩。 此色彩部分會是影像的透明的。 預設值是的洋紅色 RGB(255,0,255)。  
  
 [in] `hImageList`  
 預先載入的影像清單控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。 `FALSE`如果建立使用一般樣式 索引標籤控制項，或如果第一個方法多載無法載入指定的點陣圖`uiID`參數。  
  
### <a name="remarks"></a>備註  
 使用此方法設定 索引標籤控制項影像清單。 索引標籤的標籤旁顯示的影像清單中的映像。 這個方法會重新計算 索引標籤的高度，使  索引標籤的大小調整為包含影像和文字。  
  
 使用[CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)  索引標籤控制項，指定要顯示之影像的索引所繼承的方法。  
  
##  <a name="setresizemode"></a>CMFCTabCtrl::SetResizeMode  
 指定如何在目前的索引標籤控制項可以調整大小，然後重新顯示控制項。  
  
```  
void SetResizeMode(ResizeMode resizeMode);
```  
  
### <a name="parameters"></a>參數  
 [in] `resizeMode`  
 其中一個`CMFCTabCtrl::ResizeMode`列舉值，指定可調整大小的索引標籤控制項的方式。 如需可能值的清單，請參閱 < 備註 > 中的資料表。  
  
### <a name="remarks"></a>備註  
 `resizeMode`參數可以是下列其中一種`ResizeMode`列舉值。  
  
|名稱|描述|  
|----------|-----------------|  
|RESIZE_NO|無法調整 索引標籤控制項的大小。|  
|RESIZE_VERT|索引標籤控制項可調整大小，以垂直方式，但不是水平。|  
|RESIZE_HORIZ|索引標籤控制項可調整大小，以水平方式，但不是會以垂直方式。|  
  
##  <a name="settabmaxwidth"></a>CMFCTabCtrl::SetTabMaxWidth  
 指定在索引標籤式視窗的最大值 索引標籤寬度。  
  
```  
void SetTabMaxWidth(int nTabMaxWidth);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTabMaxWidth`  
 最大值 索引標籤的寬度，單位為像素。  
  
### <a name="remarks"></a>備註  
 使用這個方法來限制每個索引標籤中的索引標籤式視窗的寬度。 此方法相當實用的索引標籤有很長的標籤。 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)類別建構函式會初始化為 0，表示實際寬度不受限制的最大值 索引標籤寬度。  
  
##  <a name="stopresize"></a>CMFCTabCtrl::StopResize  
 終止目前的調整大小作業 索引標籤控制項上。  
  
```  
void StopResize(BOOL bCancel);
```  
  
### <a name="parameters"></a>參數  
 [in] `bCancel`  
 `TRUE`要放棄目前的調整大小作業。`FALSE`完成目前的調整大小作業。 在任一情況下，架構會停止繪製調整大小的矩形。  
  
##  <a name="synchronizescrollbar"></a>CMFCTabCtrl::SynchronizeScrollBar  
 一般索引標籤會顯示在索引標籤控制項上繪製水平捲軸。  
  
```  
BOOL SynchronizeScrollBar(SCROLLINFO* pScrollInfo = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pScrollInfo`  
 指標[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)結構或`NULL`。 此方法傳回時，而且如果此參數不是`NULL`，此結構包含捲軸上的所有參數。 預設值是 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會影響只會顯示一般索引標籤索引標籤控制項。 捲軸會同時影響所有索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)

