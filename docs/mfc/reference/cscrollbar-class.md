---
title: CScrollBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
dev_langs:
- C++
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03588a0c41633f632c99c8c178d6b69b39b00e48
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199197"
---
# <a name="cscrollbar-class"></a>CScrollBar 類別
提供 Windows 捲軸控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|建構 `CScrollBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|建立 Windows 捲軸，並將它附加至`CScrollBar`物件。|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|啟用或停用一個捲軸的一或兩個箭號。|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|擷取捲軸使用的相關資訊`SCROLLBARINFO`結構。|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|擷取捲軸的相關資訊。|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|擷取捲軸限制|  
|[CScrollBar::GetScrollPos](#getscrollpos)|擷取捲動方塊的目前位置。|  
|[CScrollBar::GetScrollRange](#getscrollrange)|擷取給定的捲軸的目前最小和最大捲軸位置。|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|設定捲軸的相關資訊。|  
|[CScrollBar::SetScrollPos](#setscrollpos)|設定捲動方塊的目前位置。|  
|[CScrollBar::SetScrollRange](#setscrollrange)|設定給定捲軸的最小和最大位置值。|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|顯示或隱藏捲軸。|  
  
## <a name="remarks"></a>備註  
 您會將捲軸控制項在兩個步驟。 首先，呼叫建構函式`CScrollBar`來建構`CScrollBar`物件，然後呼叫[建立](#create)成員函式來建立 Windows 捲軸控制項，並將其附加至`CScrollBar`物件。  
  
 如果您建立`CScrollBar` 對話方塊中 （透過對話方塊資源），物件`CScrollBar`即會自動終結，當使用者關閉對話方塊。  
  
 如果您建立`CScrollBar`物件內的視窗中，您可能也需要終結它。  
  
 如果您建立`CScrollBar`物件在堆疊上，它會自動終結。 如果您建立`CScrollBar`物件上使用堆積**新**函式，您必須呼叫**刪除**使用者終止 Windows 捲軸時終結該物件上。  
  
 如果您配置任何記憶體`CScrollBar`物件，覆寫`CScrollBar`解構函式來進行處置的配置。  
  
 如需使用的相關資訊`CScrollBar`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="create"></a>  CScrollBar::Create  
 建立 Windows 捲軸，並將它附加至`CScrollBar`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定捲軸列的樣式。 套用的任何組合[捲軸樣式](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)要捲軸。  
  
 *rect*  
 指定捲軸的大小和位置。 可以是`RECT`結構或`CRect`物件。  
  
 *pParentWnd*  
 指定捲軸列的父視窗，通常`CDialog`物件。 它必須不是 NULL。  
  
 *nID*  
 捲軸的控制項識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CScrollBar`兩個步驟中的物件。 首先，呼叫建構函式，建構`CScrollBar`物件，然後呼叫`Create`，這會建立並初始化相關聯的 Windows 捲軸，並將它附加至`CScrollBar`物件。  
  
 套用下列[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)捲軸來：  
  
- WS_CHILD 一律  
  
- WS_VISIBLE 通常  
  
- WS_DISABLED 很少  
  
- WS_GROUP 群組控制項  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar  
 建構 `CScrollBar` 物件。  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>備註  
 之後建構物件，呼叫`Create`成員函式來建立和初始化 Windows 捲軸。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar  
 啟用或停用一個捲軸的一或兩個箭號。  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>參數  
 *nArrowFlags*  
 指定捲動箭號是否已啟用或停用和啟用或停用的箭號。 這個參數可以是下列值之一：  
  
- ESB_ENABLE_BOTH 可讓這兩個捲軸的箭號。  
  
- 水平捲軸向左箭號或垂直捲軸向上箭號，會停用 ESB_DISABLE_LTUP。  
  
- 水平捲軸向右箭頭或向下的箭號，在垂直捲軸上，會停用 ESB_DISABLE_RTDN。  
  
- ESB_DISABLE_BOTH 停用這兩個捲軸的箭號。  
  
### <a name="return-value"></a>傳回值  
 如果啟用或停用指定; 箭號，非零值。否則為 0，表示箭號已要求的狀態，或發生錯誤。  
  
### <a name="example"></a>範例  
  範例，請參閱[CScrollBar::SetScrollRange](#setscrollrange)。  
  
##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo  
 擷取 `SCROLLBARINFO` 結構維護的捲軸相關資訊。  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>參數  
 *pScrollInfo*  
 指標[SCROLLBARINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollbarinfo)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬[SBM_SCROLLBARINFO](/windows/desktop/Controls/sbm-getscrollbarinfo)訊息、 Windows SDK 中所述。  
  
##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo  
 擷取 `SCROLLINFO` 結構維護的捲軸相關資訊。  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>參數  
 *lpScrollInfo*  
 指標[SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo)結構。 請參閱 Windows SDK，如需有關這個結構。  
  
 *nMask*  
 指定要擷取的捲軸列參數。 典型的用法，SIF_ALL，指定 SIF_PAGE、 SIF_POS、 SIF_TRACKPOS 和 SIF_RANGE 的組合。 請參閱`SCROLLINFO`如需有關 nMask 值。  
  
### <a name="return-value"></a>傳回值  
 如果訊息中擷取的任何值，傳回為 TRUE。 否則，它就是 FALSE。  
  
### <a name="remarks"></a>備註  
 `GetScrollInfo` 可讓應用程式使用 32 位元捲動位置。  
  
 [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo)結構包含捲軸，包括最小值和最大捲動位置、 頁面大小和捲軸方塊 （捲動方塊） 的位置的相關資訊。 請參閱`SCROLLINFO`結構變更結構的預設值的詳細資訊的 Windows SDK 中的主題。  
  
 MFC Windows 訊息，表示捲軸列位置，處理常式[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)並[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)，提供僅 16 位元的位置資料。 `GetScrollInfo` 和`SetScrollInfo`提供 32 位元的捲軸位置資料。 因此，應用程式可以呼叫`GetScrollInfo`同時處理`CWnd::OnHScroll`或`CWnd::OnVScroll`取得 32 位元捲軸列位置資料。  
  
### <a name="example"></a>範例  
  範例，請參閱[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit  
 擷取捲動捲軸位置的最大值。  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>傳回值  
 指定如果成功則為捲軸的最大值的位置否則為 0。  
  
### <a name="example"></a>範例  
  範例，請參閱[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos  
 擷取捲動方塊的目前位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定捲動方塊成功; 如果目前的位置否則為 0。  
  
### <a name="remarks"></a>備註  
 目前的位置會取決於目前的捲動範圍的相對值。 比方說，如果捲動的範圍是 100 到 200，位於中間列的捲動方塊目前位置為 150。  
  
### <a name="example"></a>範例  
  範例，請參閱[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange  
 將給定的捲軸的目前最小和最大捲軸位置複製到指定的位置*lpMinPos*並*lpMaxPos*。  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>參數  
 *lpMinPos*  
 指向要接收的最小位置的整數變數。  
  
 *lpMaxPos*  
 指向要接收的最大位置的整數變數。  
  
### <a name="remarks"></a>備註  
 捲軸控制項的預設範圍是空的 （這兩個值是 0）。  
  
### <a name="example"></a>範例  
  範例，請參閱[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo  
 設定的資訊`SCROLLINFO`結構維護的捲軸相關。  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *lpScrollInfo*  
 指標[SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo)結構。  
  
 *bRedraw*  
 指定捲軸是否應該重新繪製以反映新的資訊。 如果*bRedraw*為 TRUE 時，會重新繪製捲軸。 如果是 FALSE，會不重新繪製。 根據預設，會重新繪製捲軸。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回為 TRUE。 否則，它就是 FALSE。  
  
### <a name="remarks"></a>備註  
 您必須提供所需的值`SCROLLINFO`結構參數，包括旗標值。  
  
 `SCROLLINFO`結構包含捲軸，包括最小值和最大捲動位置、 頁面大小和捲軸方塊 （捲動方塊） 的位置的相關資訊。 請參閱[SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo)結構變更結構的預設值的詳細資訊的 Windows SDK 中的主題。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos  
 將捲動方塊的目前位置設定為所指定*nPos*而且，如果指定，會重新繪製捲軸以反映新的位置。  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *nPos*  
 指定捲動方塊的新位置。 它必須是捲動的範圍內。  
  
 *bRedraw*  
 指定捲軸是否應該重新繪製以反映新的位置。 如果*bRedraw*為 TRUE 時，會重新繪製捲軸。 如果是 FALSE，會不重新繪製。 根據預設，會重新繪製捲軸。  
  
### <a name="return-value"></a>傳回值  
 指定捲動方塊成功; 如果上一個位置否則為 0。  
  
### <a name="remarks"></a>備註  
 設定*bRedraw*設為 FALSE 時的捲軸會重新繪製另一個函式的後續呼叫若要避免在短暫的間隔內的兩次重新繪製捲軸。  
  
### <a name="example"></a>範例  
  範例，請參閱[CScrollBar::SetScrollRange](#setscrollrange)。  
  
##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange  
 設定給定捲軸的最小和最大位置值。  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *nMinPos*  
 指定捲動位置的最小值。  
  
 *nMaxPos*  
 指定捲動位置的最大值。  
  
 *bRedraw*  
 指定捲軸是否應該重新繪製以反映變更。 如果*bRedraw*為 TRUE 時，會重新繪製捲軸; 如果為 FALSE，不繪製。 根據預設，它會重新繪製。  
  
### <a name="remarks"></a>備註  
 設定*nMinPos*並*nMaxPos*為 0，以隱藏標準捲軸。  
  
 請勿呼叫這個函式來處理捲軸通知訊息時隱藏捲軸。  
  
 如果呼叫`SetScrollRange`緊接在呼叫`SetScrollPos`成員函式，設定*bRedraw*在`SetScrollPos`為 0，以防止兩次重新繪製捲軸。  
  
 所指定的值之間的差異*nMinPos*並*nMaxPos*不能大於 32,767。 捲軸控制項的預設範圍是空的 (兩者*nMinPos*並*nMaxPos*都是 0)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar  
 顯示或隱藏捲軸。  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bShow*  
 指定捲軸是否顯示或隱藏。 如果此參數為 TRUE 時，會顯示捲軸;否則它會隱藏。  
  
### <a name="remarks"></a>備註  
 應用程式不應該呼叫此函式以處理捲軸通知訊息時隱藏捲軸。  
  
### <a name="example"></a>範例  
  範例，請參閱[CScrollBar::Create](#create)。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)   
 [CComboBox 類別](../../mfc/reference/ccombobox-class.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)   
 [CStatic 類別](../../mfc/reference/cstatic-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)
