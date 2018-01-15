---
title: "CAutoHideDockSite 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8cc4e9158ae9ff2ef6fd4d48483aa5a75dd9617
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite 類別
`CAutoHideDockSite`擴充[CDockSite 類別](../../mfc/reference/cdocksite-class.md)實作自動隱藏停駐窗格。  
  
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
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指出是否`CAutoHideDockSite`窗格功能表上顯示。|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|決定是否衍生自基底的窗格物件[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)。|  
|[CAutoHideDockSite::DockPane](#dockpane)|此停駐窗格`CAuotHideDockSite`物件。|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|擷取螢幕座標中停駐位置的大小。|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|上會重新繪製窗格`CAutoHideDockSite`全域邊界與按鈕間距。|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|設定停駐列左邊的邊界。|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|將邊界設定停駐列右邊。|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|呼叫[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)上的物件`CAutoHideDockSite`。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|定義工具列和停駐列邊緣之間的間距大小。 此空間被以從左邊的緣或上邊緣，根據停駐空間的對齊方式。|  
  
## <a name="remarks"></a>備註  
 當您呼叫[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)，架構會自動建立`CAutoHideDockSite`物件。 在大部分情況下，您應該不需要具現化，或直接使用這個類別。  
  
 停駐列是停駐窗格的左半部與左邊之間的差距[CMFCAutoHideButton 類別](../../mfc/reference/cmfcautohidebutton-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取`CAutoHideDockSite`物件從`CMFCAutoHideBar`物件，以及如何設定停駐列左邊、 右邊界。  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>CAutoHideDockSite::CanAcceptPane  
 判斷是否要為基底窗格[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件或衍生自`CMFCAutoHideBar`。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `pBar`|Framework 測試基底窗格。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`pBar`衍生自`CMFCAutoHideBar`;`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 如果基底的窗格物件衍生自`CMFCAutoHideBar`，它可以包含`CAutoHideDockSite`。  
  
##  <a name="dockpane"></a>CAutoHideDockSite::DockPane  
 此停駐窗格[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)物件。  
  
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
|[輸入] `pWnd`|架構停駐窗格。|  
|[輸入] `dockMethod`|停駐窗格的選項。|  
|[輸入] `lpRect`|指定的停駐窗格界限的矩形。|  
  
### <a name="remarks"></a>備註  
 預設實作不會使用參數`dockMethod`，提供供未來使用。  
  
 如果`lpRect`是`NULL`，架構將窗格停駐位置上的預設位置。 如果水平停駐的預設位置是在最左邊的停駐位置。 否則，預設位置是在停駐的頂端。  
  
##  <a name="getalignrect"></a>CAutoHideDockSite::GetAlignRect  
 擷取螢幕座標中停駐位置的大小。  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `rect`|矩形的參考。 方法會在此矩形內，儲存停駐位置的大小。|  
  
### <a name="remarks"></a>備註  
 矩形會調整位移的邊界，使它們不包含。  
  
##  <a name="m_nextraspace"></a>CAutoHideDockSite::m_nExtraSpace  
 邊緣之間的間距大小[CAutoHideDockSite 類別](../../mfc/reference/cautohidedocksite-class.md)和[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)物件。  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>備註  
 當`CMFCAutoHideBar`停駐於`CAutoHideDockSite`，它應該不會佔用整個停駐。 這個全域變數會控制左邊或最上層框線之間的額外空間`CMFCAutoHideBar`和對應`CAutoHideDockSite`邊緣。 是否使用頂端或左邊緣，取決於目前的對齊方式。  
  
##  <a name="setoffsetleft"></a>CAutoHideDockSite::SetOffsetLeft  
 設定停駐列左邊的邊界。  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nOffset`  
 新的位移。  
  
### <a name="remarks"></a>備註  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件會以靜態方式上放置`CAutoHideDockSite`物件。 這表示使用者無法以手動方式變更的位置`CMFCAutoHideBar`物件。 `SetOffsetLeft`方法控制最左邊的左邊之間的間距`CMFCAutoHideBar`和左邊`CAutoHideDockSite`。  
  
##  <a name="setoffsetright"></a>CAutoHideDockSite::SetOffsetRight  
 將邊界設定停駐列右邊。  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nOffset`  
 新的位移。  
  
### <a name="remarks"></a>備註  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件會以靜態方式上放置`CAutoHideDockSite`物件。 這表示使用者無法以手動方式變更的位置`CMFCAutoHideBar`物件。 `SetOffsetRight`方法控制的最右邊的右側之間的間距`CMFCAutoHideBar`和右邊的 list `CAutoHideDockSite`。  
  
##  <a name="repositionpanes"></a>CAutoHideDockSite::RepositionPanes  
 上會重新繪製窗格[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)。  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `rectNewClientArea`|保留的值。|  
  
### <a name="remarks"></a>備註  
 預設實作不會使用`rectNewClientArea`。 它會重新繪製按鈕間距與全域工具列邊界的窗格。  
  
##  <a name="unsetautohidemode"></a>CAutoHideDockSite::UnSetAutoHideMode  
 呼叫[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)停駐位置上的物件。  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `pAutoHideToolbar`|指標[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)物件窗格位於`CAutoHideDockSite`。|  
  
### <a name="remarks"></a>備註  
 這個方法會搜尋包含的資料列`pAutoHideToolbar`。 它會呼叫`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`該資料列上的物件。 如果`pAutoHideToolbar`找不到或它是`NULL`，這個方法會呼叫`CMFCAutoHideBar.UnSetAutoHideMode`所有`CMFCAutoHideBar`物件`CAutoHideDockSite`。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockSite 類別](../../mfc/reference/cdocksite-class.md)
