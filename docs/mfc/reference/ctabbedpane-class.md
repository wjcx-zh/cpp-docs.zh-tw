---
title: "CTabbedPane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
dev_langs:
- C++
helpviewer_keywords:
- CTabbedPane class
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
caps.latest.revision: 27
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
ms.openlocfilehash: 70377d6be8ef4ec957c7270e501022107d4b093c
ms.lasthandoff: 02/24/2017

---
# <a name="ctabbedpane-class"></a>CTabbedPane 類別
實作具有可拆式索引標籤之窗格的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CTabbedPane::CTabbedPane`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTabbedPane::DetachPane](#detachpane)|(覆寫[CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane)。)|  
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|啟用或停用索引標籤的自動著色。|  
|[CTabbedPane::FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。 (覆寫[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|  
|[CTabbedPane::GetTabArea](#gettabarea)|傳回索引標籤式視窗內的索引標籤區域的大小和位置。|  
|[CTabbedPane::GetTabWnd](#gettabwnd)||  
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|決定索引標籤式窗格是否可切換為自動隱藏模式。 (覆寫[CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)。)|  
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|決定索引標籤是否位於視窗底部。|  
|[CTabbedPane::ResetTabs](#resettabs)|將所有的索引標籤式窗格重設為預設狀態。|  
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|設定在自動套色功能啟用時可以使用的自訂色彩清單。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|應用程式中的索引標籤的預設位置。|  
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。|  
  
## <a name="remarks"></a>備註  
 當使用者指向第二個窗格的標題，將一個窗格附加到另一個窗格時，架構會自動建立此類別的執行個體。 架構所建立的所有索引標籤式窗格，ID 皆為 -1。  
  
 若要指定一般索引標籤，而非 Outlook 樣式索引標籤，請將傳遞`AFX_CBRS_REGULAR_TABS`樣式來[CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex)方法。  
  
 如果您建立具有可卸離索引標籤的索引標籤式窗格，架構可能會自動終結該窗格，因此您不應儲存指標。 若要取得索引標籤式窗格的指標，請呼叫 `CBasePane::GetParentTabbedPane` 方法。  
  
## <a name="example"></a>範例  
 在此範例中，我們會建立 `CTabbedPane` 物件。 接下來，我們使用[CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab)附加額外的索引標籤。  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),  
    TRUE, 
 (UINT) -1,  
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
    WS_CLIPCHILDREN | CBRS_LEFT |    
    CBRS_FLOAT_MULTI)) 
{  
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create  
}  
 
pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```  
  
## <a name="example"></a>範例  
 若要建立索引標籤式的控制列物件的另一種方式是使用[CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)。 `AttachToTabWnd`方法以動態方式建立索引標籤式的窗格物件，使用所設定的執行階段類別資訊[CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)。  
  
 在此範例中，我們會以動態方式建立索引標籤式窗格、附加兩個索引標籤，然後使第二個索引標籤無法卸離。  
  
```  
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxTabbedPane.h  
  
##  <a name="detachpane"></a>CTabbedPane::DetachPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 [in] `bHide`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor  
 啟用或停用索引標籤的自動著色。  
  
```  
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要啟用自動著色的索引標籤。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個靜態方法，啟用或停用自動著色的應用程式中的所有索引標籤式窗格中的索引標籤。 啟用這項功能時，每個索引標籤會依自己的色彩填滿。 您可以找到用來呼叫色彩索引標籤的色彩清單[CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors)方法。  
  
 您可以指定將用於藉由呼叫索引標籤的色彩清單[CTabbedPane::SetTabAutoColors](#settabautocolors)。  
  
 根據預設，此選項已停用。  
  
##  <a name="floattab"></a>CTabbedPane::FloatTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 [in] `nTabID`  
 [in] `dockMethod`  
 [in] `bHide`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettabarea"></a>CTabbedPane::GetTabArea  
 索引標籤式視窗中傳回的大小和索引標籤區域位置。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectTabAreaTop`  
 包含的大小和位置，在螢幕座標中的最上層索引標籤區域。  
  
 [輸出] `rectTabAreaBottom`  
 包含的大小和位置，在螢幕座標中下方的索引標籤區域。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以判斷如何停駐使用者拖曳窗格。 當使用者拖曳窗格的 [目標] 窗格的索引標籤區域上時，架構會嘗試將它新增為新的索引標籤的 [目標] 窗格。 否則，嘗試將目標窗格中，牽涉到建立新的窗格容器與用來分隔兩個窗格的窗格分割線的一端停駐窗格。  
  
 覆寫這個方法在`CTabbedPane`-衍生的類別，來變更此行為。  
  
##  <a name="gettabwnd"></a>CTabbedPane::GetTabWnd  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCTabCtrl* GetTabWnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom  
 決定索引標籤是否位於視窗底部。  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤區域位於底部的索引標籤式視窗。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop  
 應用程式中的索引標籤的預設位置。  
  
```  
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;  
```  
  
### <a name="remarks"></a>備註  
 這個靜態成員設定為`TRUE`以強制在索引標籤式窗格的頂端顯示應用程式中的所有索引標籤。  
  
 在建立索引標籤式的窗格之前，您必須將此值。  
  
 預設值是 `FALSE`。  
  
##  <a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC  
 自訂 `CMFCTabCtrl` 衍生物件的執行階段類別資訊。  
  
```  
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;  
```  
  
### <a name="remarks"></a>備註  
 設定此靜態成員變數的執行階段類別資訊的指標`CMFCTabCtrl`-衍生物件，如果您使用自訂的索引標籤式的視窗，在索引標籤式窗格。  
  
##  <a name="resettabs"></a>CTabbedPane::ResetTabs  
 將所有的索引標籤式窗格重設為預設狀態。  
  
```  
static void ResetTabs();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，將會還原成預設狀態的所有索引標籤式的窗格。 呼叫時，這個方法會重設的框線大小和自動色彩狀態的所有索引標籤式窗格。  
  
##  <a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors  
 設定啟用自動色彩功能時所使用的自訂色彩的清單。  
  
```  
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>參數  
 [in] `arColors`  
 包含要設定色彩的陣列。  
  
### <a name="remarks"></a>備註  
 使用這個方法來自訂已啟用自動色彩功能時所使用的色彩清單。 這是靜態函式，而且會影響您的應用程式中的所有索引標籤式的窗格。  
  
 使用[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)啟用或停用自動色彩功能。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)

