---
title: "CScrollBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CScrollBar
dev_langs:
- C++
helpviewer_keywords:
- CScrollBar class
- SCROLLBAR window class
- scroll bars
- Windows common controls [C++], CScrollBar
- controls [MFC], scroll bar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
caps.latest.revision: 21
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
ms.openlocfilehash: 84b59f041f1a6cf73843c303e1a6b71adffc2101
ms.lasthandoff: 02/24/2017

---
# <a name="cscrollbar-class"></a>CScrollBar 類別
提供 Windows 捲軸控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|建構 `CScrollBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|建立 Windows 捲軸，並將它附加`CScrollBar`物件。|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|啟用或停用一個捲軸的一或兩個箭號。|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|擷取資訊捲軸使用`SCROLLBARINFO`結構。|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|擷取捲軸的相關資訊。|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|擷取捲軸的限制|  
|[CScrollBar::GetScrollPos](#getscrollpos)|擷取捲動方塊的目前位置。|  
|[CScrollBar::GetScrollRange](#getscrollrange)|擷取給定的捲軸列的目前最小和最大的捲軸位置。|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|設定捲軸的相關資訊。|  
|[CScrollBar::SetScrollPos](#setscrollpos)|設定目前的捲動方塊的位置。|  
|[CScrollBar::SetScrollRange](#setscrollrange)|設定給定捲軸的最小和最大位置值。|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|顯示或隱藏捲軸。|  
  
## <a name="remarks"></a>備註  
 您在兩個步驟中建立的捲軸控制項。 首先，呼叫建構函式`CScrollBar`建構`CScrollBar`物件，然後呼叫[建立](#create)成員函式來建立 Windows 捲軸控制項，並將其附加至`CScrollBar`物件。  
  
 如果您建立`CScrollBar`（透過對話方塊資源），對話方塊內的物件`CScrollBar`即會自動終結，當使用者關閉對話方塊。  
  
 如果您建立`CScrollBar`視窗中，您可能也需要它終結物件。  
  
 如果您建立`CScrollBar`物件在堆疊上，它會自動終結。 如果您建立`CScrollBar`使用堆積上的物件**新**函式，您必須呼叫**刪除**使用者終止 Windows 捲軸時終結該物件上。  
  
 如果您配置任何記憶體`CScrollBar`物件，覆寫`CScrollBar`解構函式配置的處置。  
  
 如需使用的相關資訊`CScrollBar`，請參閱[控制項](../../mfc/controls-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecreatea--cscrollbarcreate"></a><a name="create"></a>CScrollBar::Create  
 建立 Windows 捲軸，並將它附加`CScrollBar`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定捲軸列的樣式。 套用的任何結合[捲軸樣式](../../mfc/reference/scroll-bar-styles.md)至捲軸。  
  
 `rect`  
 指定的捲軸的大小和位置。 可以是`RECT`結構或`CRect`物件。  
  
 `pParentWnd`  
 指定捲軸列的父視窗，通常`CDialog`物件。 它不得為**NULL**。  
  
 `nID`  
 捲軸控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CScrollBar`兩個步驟中的物件。 首先，呼叫建構函式，建構`CScrollBar`物件，然後呼叫**建立**，這會建立和初始化相關聯的 Windows 捲軸，並附加它`CScrollBar`物件。  
  
 適用於下列[視窗樣式](../../mfc/reference/window-styles.md)捲軸來︰  
  
- **WS_CHILD**一律  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_GROUP**控制項群組  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar #&1;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="a-namecscrollbara--cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar  
 建構 `CScrollBar` 物件。  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>備註  
 之後建構物件，呼叫**建立**成員函式來建立和初始化 Windows 捲軸。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar #&2;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="a-nameenablescrollbara--cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar  
 啟用或停用一個捲軸的一或兩個箭號。  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>參數  
 `nArrowFlags`  
 指定是否啟用或停用捲動箭號，以及啟用或停用的箭號。 這個參數可以是下列值之一︰  
  
- **ESB_ENABLE_BOTH**可讓這兩個捲軸之捲動箭號。  
  
- **ESB_DISABLE_LTUP**停用水平捲軸向的左鍵或向上箭號的垂直捲軸。  
  
- **ESB_DISABLE_RTDN**水平捲軸向右箭號或向下箭號，垂直捲軸的停用。  
  
- **ESB_DISABLE_BOTH**停用這兩個捲軸之捲動箭號。  
  
### <a name="return-value"></a>傳回值  
 箭號，啟用或停用所指定; 如果為非零否則為 0，表示箭號，已在要求的狀態或發生錯誤。  
  
### <a name="example"></a>範例  
  請參閱範例[CScrollBar::SetScrollRange](#setscrollrange)。  
  
##  <a name="a-namegetscrollbarinfoa--cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo  
 擷取的資訊， **SCROLLBARINFO**結構會維護有關捲軸。  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>參數  
 *pScrollInfo*  
 指標[SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535)結構。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetscrollinfoa--cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo  
 擷取 `SCROLLINFO` 結構維護的捲軸相關資訊。  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>參數  
 `lpScrollInfo`  
 指標[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)結構。 請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關此結構。  
  
 `nMask`  
 指定要擷取的捲軸列參數。 典型的用法，SIF_ALL，指定 SIF_PAGE、 SIF_POS、 SIF_TRACKPOS 和 SIF_RANGE 的組合。 請參閱`SCROLLINFO`如需有關 nMask 值。  
  
### <a name="return-value"></a>傳回值  
 如果訊息中擷取的任何值，傳回是**TRUE**。 否則，它是**FALSE**。  
  
### <a name="remarks"></a>備註  
 `GetScrollInfo`可讓應用程式使用 32 位元的捲動位置。  
  
 [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)結構包含捲軸，包括最小值和最大值捲動位置，頁面大小和捲軸方塊 （捲動方塊） 的位置相關資訊。 請參閱`SCROLLINFO`結構中的主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關變更結構的預設值。  
  
 MFC 視窗訊息處理常式，以指出捲軸列的位置， [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)和[CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)，提供僅 16 位元的位置資料。 `GetScrollInfo`和`SetScrollInfo`提供 32 位元的捲軸位置的資料。 因此，應用程式可以呼叫`GetScrollInfo`時處理`CWnd::OnHScroll`或`CWnd::OnVScroll`取得 32 位元捲軸位置資料。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="a-namegetscrolllimita--cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit  
 擷取捲動捲軸位置的最大值。  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>傳回值  
 指定如果成功，捲軸的最大位置否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="a-namegetscrollposa--cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos  
 擷取捲動方塊的目前位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定的捲動方塊成功; 如果目前的位置否則為 0。  
  
### <a name="remarks"></a>備註  
 目前的位置是取決於目前的捲動範圍的相對值。 例如，如果捲動的範圍是 100 到 200，捲動方塊列中間，目前位置為 150。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="a-namegetscrollrangea--cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange  
 將給定的捲軸列的目前最小和最大的捲軸位置複製到指定的位置`lpMinPos`和`lpMaxPos`。  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpMinPos`  
 指向要接收的最小位置的整數變數。  
  
 `lpMaxPos`  
 指向要接收的最大位置的整數變數。  
  
### <a name="remarks"></a>備註  
 捲軸控制項的預設範圍是空的 （這兩個值是 0）。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。  
  
##  <a name="a-namesetscrollinfoa--cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo  
 設定的資訊`SCROLLINFO`結構會維護有關捲軸。  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpScrollInfo`  
 指標[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)結構。  
  
 `bRedraw`  
 指定的捲軸是否應該重新繪製以反映新的資訊。 如果`bRedraw`是**TRUE**，重繪捲軸時。 如果是**FALSE**，不會重新繪製。 根據預設，捲軸會重新繪製。  
  
### <a name="return-value"></a>傳回值  
 如果成功，傳回是**TRUE**。 否則，它是**FALSE**。  
  
### <a name="remarks"></a>備註  
 您必須提供所需的值`SCROLLINFO`結構的參數，包括旗標值。  
  
 `SCROLLINFO`結構包含捲軸，包括最小值和最大值捲動位置，頁面大小和捲軸方塊 （捲動方塊） 的位置相關資訊。 請參閱[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)結構中的主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關變更結構的預設值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar #&3;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="a-namesetscrollposa--cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos  
 將目前捲動方塊的位置設定為指定的`nPos`，如果指定，會重繪捲軸，以反映新的位置。  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 指定捲動方塊的新位置。 它必須捲動的範圍內。  
  
 `bRedraw`  
 指定的捲軸是否應該重新繪製以反映新的位置。 如果`bRedraw`是**TRUE**，重繪捲軸時。 如果是**FALSE**，不會重新繪製。 根據預設，捲軸會重新繪製。  
  
### <a name="return-value"></a>傳回值  
 指定前一個位置的捲動方塊，如果登錄成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 設定`bRedraw`至**FALSE**捲軸的後續呼叫另一個函式，以避免重繪較短的間隔內的兩倍的捲軸的繪製時。  
  
### <a name="example"></a>範例  
  請參閱範例[CScrollBar::SetScrollRange](#setscrollrange)。  
  
##  <a name="a-namesetscrollrangea--cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange  
 設定給定捲軸的最小和最大位置值。  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nMinPos`  
 指定捲動位置的最小值。  
  
 `nMaxPos`  
 指定捲動位置的最大值。  
  
 `bRedraw`  
 指定的捲軸是否應該重新繪製以反映變更。 如果`bRedraw`是**TRUE**，捲軸重繪時; 如果**FALSE**，不會重新繪製。 它會在預設情況下重新繪製。  
  
### <a name="remarks"></a>備註  
 設定`nMinPos`和`nMaxPos`為 0，以隱藏標準捲軸。  
  
 請勿呼叫此函式可處理的捲軸的通知訊息時隱藏捲軸。  
  
 如果呼叫`SetScrollRange`緊接在後面的呼叫`SetScrollPos`設定成員函式，`bRedraw`中`SetScrollPos`為 0，以防止重繪的兩倍的捲軸。  
  
 所指定的值之間的差異`nMinPos`和`nMaxPos`不能大於 32767。 捲軸控制項的預設範圍是空的 (兩者`nMinPos`和`nMaxPos`都是 0)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CScrollBar #&4;](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="a-nameshowscrollbara--cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::ShowScrollBar  
 顯示或隱藏捲軸。  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bShow`  
 指定顯示或隱藏捲軸。 如果這個參數是**TRUE**，顯示捲軸，否則會隱藏起來。  
  
### <a name="remarks"></a>備註  
 應用程式不應該呼叫此函式可處理的捲軸的通知訊息時隱藏捲軸。  
  
### <a name="example"></a>範例  
  請參閱範例[CScrollBar::Create](#create)。  
  
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

