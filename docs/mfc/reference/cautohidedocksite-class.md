---
title: CAutoHideDockSite 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
dev_langs:
- C++
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f36d6231cfce86314be082a77a39034b619741ad
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336939"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 類別
`CAutoHideDockSite`擴充[CDockSite 類別](../../mfc/reference/cdocksite-class.md)以實作自動隱藏固定窗格。  
  
## <a name="syntax"></a>語法  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CAutoHideDockSite::CAutoHideDockSite`|建構 `CAutoHideDockSite` 物件。|  
|`CAutoHideDockSite::~CAutoHideDockSite`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指出是否`CAutoHideDockSite`窗格功能表上會顯示。|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|決定是否要將基底的窗格物件衍生自[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)。|  
|[CAutoHideDockSite::DockPane](#dockpane)|這將窗格停駐於`CAuotHideDockSite`物件。|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|擷取停駐站台，以螢幕座標表示的大小。|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|會窗格上重新繪製`CAutoHideDockSite`具有通用的邊界與按鈕間距。|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|設定停駐列左邊的邊界。|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|設定停駐列右邊的邊界。|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|呼叫[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)上的物件`CAutoHideDockSite`。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|定義工具列和停駐列邊緣之間的間距的大小。 此空間被測量從左邊的緣或上邊緣，根據停駐空間的對齊方式。|  
  
## <a name="remarks"></a>備註  
 當您呼叫[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)，架構會自動建立`CAutoHideDockSite`物件。 在大部分情況下，您不應該具現化，或直接使用這個類別。  
  
 停駐列是停駐窗格左下的方和左下的方之間的差距[CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取`CAutoHideDockSite`物件從`CMFCAutoHideBar`物件，以及如何將停駐列左邊和右邊邊界設定。  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>  CAutoHideDockSite::CanAcceptPane  
 判斷基底的窗格是否[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件或衍生自`CMFCAutoHideBar`。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*pBar*|Framework 測試 [基底] 窗格。|  
  
### <a name="return-value"></a>傳回值  
 則為 TRUE *pBar*衍生自`CMFCAutoHideBar`;FALSE 否則。  
  
### <a name="remarks"></a>備註  
 如果基底的窗格物件衍生自`CMFCAutoHideBar`，它可以包含`CAutoHideDockSite`。  
  
##  <a name="dockpane"></a>  CAutoHideDockSite::DockPane  
 窗格停駐於這[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)物件。  
  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*pWnd*|Framework 停駐窗格。|  
|[in]*dockMethod*|停駐窗格的選項。|  
|[in]*lpRect*|指定停駐窗格的界限的矩形。|  
  
### <a name="remarks"></a>備註  
 預設實作不會使用參數*dockMethod*，其可供未來使用。  
  
 如果*lpRect*是 NULL 時，framework 將窗格停駐位置的預設位置。 如果水平停駐位置，預設位置是在最左邊的停駐位置。 否則的預設位置是在停駐位置的頂端。  
  
##  <a name="getalignrect"></a>  CAutoHideDockSite::GetAlignRect  
 擷取停駐站台，以螢幕座標表示的大小。  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*rect*|矩形的參考。 方法會儲存停駐位置的大小，這個矩形中。|  
  
### <a name="remarks"></a>備註  
 這樣就不必包含矩形被調整位移的邊界。  
  
##  <a name="m_nextraspace"></a>  CAutoHideDockSite::m_nExtraSpace  
 邊緣之間的間距大小[CAutoHideDockSite 類別](../../mfc/reference/cautohidedocksite-class.md)並[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)物件。  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>備註  
 當`CMFCAutoHideBar`停駐於`CAutoHideDockSite`，它應該不會佔用整個停駐位置。 這個全域變數會控制的左方或上方框線之間的額外空間`CMFCAutoHideBar`和對應`CAutoHideDockSite`邊緣。 是否使用上方或左方邊緣取決於目前的對齊方式。  
  
##  <a name="setoffsetleft"></a>  CAutoHideDockSite::SetOffsetLeft  
 設定停駐列左邊的邊界。  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>參數  
 [in]*nOffset*  
 新的位移。  
  
### <a name="remarks"></a>備註  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件會以靜態方式上放置`CAutoHideDockSite`物件。 這表示使用者無法以手動方式變更的位置`CMFCAutoHideBar`物件。 `SetOffsetLeft`方法控制最左邊的左下方之間的間距`CMFCAutoHideBar`左邊的`CAutoHideDockSite`。  
  
##  <a name="setoffsetright"></a>  CAutoHideDockSite::SetOffsetRight  
 設定停駐列右邊的邊界。  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>參數  
 [in]*nOffset*  
 新的位移。  
  
### <a name="remarks"></a>備註  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件會以靜態方式上放置`CAutoHideDockSite`物件。 這表示使用者無法以手動方式變更的位置`CMFCAutoHideBar`物件。 `SetOffsetRight`方法控制之間的最右邊的右側的間距`CMFCAutoHideBar`和右側`CAutoHideDockSite`。  
  
##  <a name="repositionpanes"></a>  CAutoHideDockSite::RepositionPanes  
 會窗格上重新繪製[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)。  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*rectNewClientArea*|保留的值。|  
  
### <a name="remarks"></a>備註  
 預設實作不會使用*rectNewClientArea*。 它會重新繪製邊界全域工具列和按鈕間距的窗格。  
  
##  <a name="unsetautohidemode"></a>  CAutoHideDockSite::UnSetAutoHideMode  
 呼叫[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)停駐位置上的物件。  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in]*pAutoHideToolbar*|指標[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件 窗格位於`CAutoHideDockSite`。|  
  
### <a name="remarks"></a>備註  
 這個方法會搜尋包含的資料列*pAutoHideToolbar*。 它會呼叫`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`該資料列上的物件。 如果*pAutoHideToolbar*找不到或它是 NULL，這個方法會呼叫`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`物件上`CAutoHideDockSite`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockSite 類別](../../mfc/reference/cdocksite-class.md)
