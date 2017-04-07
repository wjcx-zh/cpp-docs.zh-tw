---
title: "CReBarCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
dev_langs:
- C++
helpviewer_keywords:
- rebar controls, control bar
- rebar controls, CReBarCtrl class
- CReBarCtrl class
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 23
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
ms.openlocfilehash: c1da4de2897c74e9cb25bc060033f4bd43159174
ms.lasthandoff: 02/24/2017

---
# <a name="crebarctrl-class"></a>CReBarCtrl 類別
封裝 Rebar 控制項的功能，這個控制項是子視窗的容器。  
  
## <a name="syntax"></a>語法  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|建構 `CReBarCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](#begindrag)|Rebar 控制項置於拖放模式中。|  
|[CReBarCtrl::Create](#create)|建立 rebar 控制項並將它附加`CReBarCtrl`物件。|  
|[CReBarCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立 rebar 控制項，並附加至該`CReBarCtrl`物件。|  
|[CReBarCtrl::DeleteBand](#deleteband)|從 rebar 控制項刪除群組列。|  
|[CReBarCtrl::DragMove](#dragmove)|呼叫之後，會更新 rebar 控制項中的拖放到位置`BeginDrag`。|  
|[CReBarCtrl::EndDrag](#enddrag)|終止 rebar 控制項的拖放作業。|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|擷取訊號範圍的框線。|  
|[CReBarCtrl::GetBandCount](#getbandcount)|擷取目前在 rebar 控制項群組列的計數。|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|擷取指定的群組列 rebar 控制項中的相關資訊。|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|擷取之群組列的邊界。|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|擷取 rebar 控制項的高度。|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|擷取 rebar 控制項和它所使用的影像清單的相關資訊。|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|擷取 rebar 控制項的預設背景色彩。|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|擷取[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)rebar 控制項相關聯的結構。|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|擷取 rebar 控制項的`IDropTarget`介面指標。|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|取得目前的 rebar 控制項的延伸的樣式。|  
|[CReBarCtrl::GetImageList](#getimagelist)|擷取映像清單與 rebar 控制項相關聯。|  
|[CReBarCtrl::GetPalette](#getpalette)|擷取目前的 rebar 控制項的調色盤。|  
|[CReBarCtrl::GetRect](#getrect)|擷取指定之群組列 rebar 控制項中的週框。|  
|[CReBarCtrl::GetRowCount](#getrowcount)|擷取頻外 rebar 控制項中的資料列數目。|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|擷取 rebar 控制項中指定的資料列的高度。|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|擷取 rebar 控制項的預設文字色彩。|  
|[CReBarCtrl::GetToolTips](#gettooltips)|擷取與 rebar 控制項相關聯的任何工具提示控制項的控制代碼。|  
|[CReBarCtrl::HitTest](#hittest)|判斷 rebar 群組列的部份特定時點在畫面上，如果 rebar 群組列在該點存在。|  
|[CReBarCtrl::IDToIndex](#idtoindex)|將群組列中的索引 rebar 控制項的訊號範圍識別項 (ID)。|  
|[Crebarctrl:: Insertband](#insertband)|Rebar 控制項中插入新的群組列。|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|調整為其最大大小 rebar 控制項中的之群組列的大小。|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|調整為其最小大小 rebar 控制項中的之群組列的大小。|  
|[CReBarCtrl::MoveBand](#moveband)|移動到另一個索引帶。|  
|[CReBarCtrl::PushChevron](#pushchevron)|以程式設計方式將推入的 > 形箭號。|  
|[CReBarCtrl::RestoreBand](#restoreband)|調整為其理想大小 rebar 控制項中的之群組列。|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Rebar 控制項中設定現有的群組列的特性。|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|在目前的 rebar 控制項中設定指定固定的寬度。|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|設定 rebar 控制項的特性。|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|設定 rebar 控制項的預設背景色彩。|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Rebar 控制項上設定按鈕的色彩配置。|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|設定目前的 rebar 控制項的延伸的樣式。|  
|[CReBarCtrl::SetImageList](#setimagelist)|設定 rebar 控制項的影像清單。|  
|[CReBarCtrl::SetOwner](#setowner)|設定 rebar 控制項的主控視窗。|  
|[CReBarCtrl::SetPalette](#setpalette)|設定目前的 rebar 控制項的調色盤。|  
|[CReBarCtrl::SetTextColor](#settextcolor)|將 rebar 控制項的預設文字色彩。|  
|[CReBarCtrl::SetToolTips](#settooltips)|將工具提示控制項與 rebar 控制項產生關聯。|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|設定 rebar 控制項的視覺化樣式。|  
|[CReBarCtrl::ShowBand](#showband)|顯示或隱藏 rebar 控制項中的指定之群組列。|  
|[CReBarCtrl::SizeToRect](#sizetorect)|符合指定的矩形 rebar 控制項。|  
  
## <a name="remarks"></a>備註  
 Rebar 控制項所在的應用程式會指派至 rebar 群組列的 rebar 控制項所包含的子視窗。 子視窗是通常是另一個常見的控制項。  
  
 Rebar 控制項包含一或多個群組列。 每個群組列可以包含移駐夾列、 點陣圖、 文字標籤和子視窗的組合。 還可以包含的每一個項目其中之一。  
  
 Rebar 控制項可以在指定的背景點陣圖上顯示的子視窗。 所有的 rebar 控制項可以調整大小，除了使用**RBBS_FIXEDSIZE**樣式。 當您重新調整位置，或調整 rebar 控制項的大小，rebar 控制項管理的大小和位置指派給該群組列的子視窗。 若要調整大小或變更控制項中的群組列的順序，按一下並拖曳群組列的移駐夾列。  
  
 下圖顯示具有三個群組列的 rebar 控制項︰  
  
-   0 包含一般、 透明工具列控制項。  
  
-   1 是包含兩個透明的標準和透明下拉式按鈕。  
  
-   2 包含下拉式方塊和四個標準按鈕。  
  
     ![Rebar 功能表範例](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Rebar 控制項  
 Rebar 控制項的支援︰  
  
-   影像清單。  
  
-   訊息處理。  
  
-   自訂繪圖功能。  
  
-   各種不同的控制項樣式，除了標準的視窗樣式。 如需這些樣式的清單，請參閱[Rebar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="begindrag"></a>CReBarCtrl::BeginDrag  
 實作的 Win32 訊息的行為[RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 拖放作業將會影響的群組列的以零為起始索引。  
  
 `dwPos`  
 A`DWORD`包含開始滑鼠座標值。 水平座標包含在 LOWORD 而且 HIWORD 中包含的垂直座標。 如果您傳遞`(DWORD)-1`，rebar 控制項將使用上一次呼叫控制項的執行緒的滑鼠位置**GetMessage**或**PeekMessage**。  
  
##  <a name="create"></a>CReBarCtrl::Create  
 建立 rebar 控制項並將它附加`CReBarCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定 rebar 控制項的樣式套用至控制項的組合。 請參閱[Rebar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]支援樣式的清單。  
  
 `rect`  
 參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，也就是 rebar 控制項的大小與位置。  
  
 `pParentWnd`  
 指標[CWnd](../../mfc/reference/cwnd-class.md) rebar 控制項的父視窗的物件。 它不得為**NULL**。  
  
 `nID`  
 指定 rebar 控制項的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 非零，如果物件建立成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 建立 rebar 控制項中的兩個步驟︰  
  
1.  呼叫[CReBarCtrl](#crebarctrl)建構`CReBarCtrl`物件。  
  
2.  呼叫此成員函式，建立 Windows rebar 控制項並將它附加`CReBarCtrl`物件。  
  
 當您呼叫**建立**，通用控制項都已初始化。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&3;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CReBarCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CReBarCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定 rebar 控制項的樣式套用至控制項的組合。 如需支援的樣式，請參閱[Rebar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
##  <a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl  
 建立 `CReBarCtrl` 物件。  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>範例  
  請參閱範例[CReBarCtrl::Create](#create)。  
  
##  <a name="deleteband"></a>CReBarCtrl::DeleteBand  
 實作的 Win32 訊息的行為[RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 要刪除的群組列的以零為起始索引。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功; 刪除群組列否則為零。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&4;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>CReBarCtrl::DragMove  
 實作的 Win32 訊息的行為[RB_DRAGMOVE](https://msdn.microsoft.com/library/bb774433.aspx)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>參數  
 `dwPos`  
 A`DWORD`值，其中包含新的滑鼠座標。 水平座標包含在 LOWORD 而且 HIWORD 中包含的垂直座標。 如果您傳遞`(DWORD)-1`，rebar 控制項將使用上一次呼叫控制項的執行緒的滑鼠位置**GetMessage**或**PeekMessage**。  
  
##  <a name="enddrag"></a>CReBarCtrl::EndDrag  
 實作的 Win32 訊息的行為[RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>CReBarCtrl::GetBandBorders  
 實作的 Win32 訊息的行為[RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 框線會擷取的群組列的以零為起始索引。  
  
 `prc`  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，將會收到的訊號範圍的框線。 Rebar 控制項有**RBS_BANDBORDERS**樣式，此結構的每個成員會收到的像素數，一端對應的寬線，構成框線。 如果沒有 rebar 控制項**RBS_BANDBORDERS**樣式，僅此結構的左的成員收到有效的資訊。 Rebar 控制項樣式的說明，請參閱[Rebar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbandcount"></a>CReBarCtrl::GetBandCount  
 實作的 Win32 訊息的行為[RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指派給控制項群組列的數目。  
  
##  <a name="getbandinfo"></a>CReBarCtrl::GetBandInfo  
 實作的 Win32 訊息的行為[RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 擷取資訊的群組列的以零為起始索引。  
  
 `prbbi`  
 指標[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)接收訊號範圍資訊的結構。 您必須設定`cbSize`此結構的成員`sizeof(REBARBANDINFO)`，並設定**fMask**成員到您想要傳送此訊息之前擷取的項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="getbandmargins"></a>CReBarCtrl::GetBandMargins  
 擷取寬線的邊界。  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>參數  
 *pMargins*  
 指標[邊界](http://msdn.microsoft.com/library/windows/desktop/bb773244)來接收資訊的結構。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbarheight"></a>CReBarCtrl::GetBarHeight  
 擷取 rebar 列的高度。  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示高度，單位為像素控制項。  
  
##  <a name="getbarinfo"></a>CReBarCtrl::GetBarInfo  
 實作的 Win32 訊息的行為[RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>參數  
 `prbi`  
 指標[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)結構，將會收到 rebar 控制項資訊。 您必須設定`cbSize`此結構的成員`sizeof(REBARINFO)`傳送此訊息之前。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="getbkcolor"></a>CReBarCtrl::GetBkColor  
 實作的 Win32 訊息的行為[RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，代表目前的預設背景色彩。  
  
##  <a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme  
 擷取[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)rebar 控制項的結構。  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>參數  
 `lpcs`  
 指標[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 **新增的色彩配置**結構包含按鈕醒目提示色彩和陰影色彩。  
  
##  <a name="getdroptarget"></a>CReBarCtrl::GetDropTarget  
 實作的 Win32 訊息的行為[RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)介面。  
  
##  <a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle  
 取得目前的 rebar 控制項的延伸的樣式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位元組合 (OR) 旗標，表示延伸的樣式。 可能的旗標為`RBS_EX_SPLITTER`和`RBS_EX_TRANSPARENT`。 如需詳細資訊，請參閱`dwMask`參數[CReBarCtrl::SetExtendedStyle](#setextendedstyle)方法。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getimagelist"></a>CReBarCtrl::GetImageList  
 取得`CImageList`rebar 控制項相關聯的物件。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。 傳回**NULL**如果沒有映像清單控制項的設定。  
  
### <a name="remarks"></a>備註  
 此成員函式會使用儲存在大小和遮罩資訊[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getpalette"></a>CReBarCtrl::GetPalette  
 擷取目前的 rebar 控制項的調色盤。  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CPalette](../../mfc/reference/cpalette-class.md)物件，指定 rebar 控制項目前的調色盤。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式使用`CPalette`物件做為其傳回值，而不要用`HPALETTE`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&5;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>CReBarCtrl::GetRect  
 實作的 Win32 訊息的行為[RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 在 rebar 控制項群組列的以零起始的索引。  
  
 `prc`  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，將會收到 rebar 群組列的界限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&6;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>CReBarCtrl::GetRowCount  
 實作的 Win32 訊息的行為[RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **UINT**值，表示控制項中的群組列資料列數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&7;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>CReBarCtrl::GetRowHeight  
 實作的 Win32 訊息的行為[RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>參數  
 *uRow*  
 必須擷取其高度的群組列的以零為起始索引。  
  
### <a name="return-value"></a>傳回值  
 A **UINT**值，表示資料列高度，單位為像素。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&8;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>CReBarCtrl::GetTextColor  
 實作的 Win32 訊息的行為[RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，代表目前的預設文字色彩。  
  
##  <a name="gettooltips"></a>CReBarCtrl::GetToolTips  
 實作的 Win32 訊息的行為[RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件。  
  
### <a name="remarks"></a>備註  
 請注意，MFC 實作`GetToolTips`傳回的指標`CToolTipCtrl`，而不要用`HWND`。  
  
##  <a name="hittest"></a>CReBarCtrl::HitTest  
 實作的 Win32 訊息的行為[RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>參數  
 *prbht*  
 指標[RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391)結構。 在傳送訊息之前**pt**這個結構的成員必須初始化為所要測試，在工作區座標的點。  
  
### <a name="return-value"></a>傳回值  
 在指定的點，則為-1 之處，已沒有 rebar 群組列還寬的以零為起始的索引。  
  
##  <a name="idtoindex"></a>CReBarCtrl::IDToIndex  
 實作的 Win32 訊息的行為[RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>參數  
 *uBandID*  
 指定的群組列的應用程式定義識別碼傳入**wID**成員[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)結構插入群組列時。  
  
### <a name="return-value"></a>傳回值  
 以零為起始的訊號範圍索引，如果成功或為-1。 如果存在重複的訊號範圍的索引，則會傳回第一個。  
  
##  <a name="insertband"></a>Crebarctrl:: Insertband  
 實作的 Win32 訊息的行為[RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>參數  
 *uIndex*  
 群組列插入之位置的以零為起始的索引。 如果您將此參數設定為-1 時，控制會加入新的訊號範圍的最後一個位置。  
  
 `prbbi`  
 指標[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)結構，定義要插入列。 您必須設定`cbSize`此結構的成員`sizeof(REBARBANDINFO)`之前呼叫這個函式。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&9;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>CReBarCtrl::MaximizeBand  
 調整為其最大大小 rebar 控制項中的之群組列的大小。  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 要最大化的群組列的以零為起始索引。  
  
### <a name="remarks"></a>備註  
 實作的 Win32 訊息的行為[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)與`fIdeal`中所述，設定為 0， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&10;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>CReBarCtrl::MinimizeBand  
 調整為其最小大小 rebar 控制項中的之群組列的大小。  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 最小化的群組列的以零為起始索引。  
  
### <a name="remarks"></a>備註  
 實作的 Win32 訊息的行為[RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&11;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>CReBarCtrl::MoveBand  
 實作的 Win32 訊息的行為[RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>參數  
 *uFrom*  
 要移動的群組列的以零為起始索引。  
  
 *uTo*  
 列的新位置的以零為起始的索引。 此參數值必須永遠不會大於減一的群組列的數目。 若要取得的區間數目，請呼叫[GetBandCount](#getbandcount)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="pushchevron"></a>CReBarCtrl::PushChevron  
 實作的 Win32 訊息的行為[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 以零為起始的 > 形箭號會發送訊號範圍的索引。  
  
 `lAppValue`  
 應用程式定義的 32 位元值。 請參閱`lAppValue`中[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="restoreband"></a>CReBarCtrl::RestoreBand  
 調整為其理想大小 rebar 控制項中的之群組列。  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 要最大化的群組列的以零為起始索引。  
  
### <a name="remarks"></a>備註  
 實作的 Win32 訊息的行為[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)與`fIdeal`中所述，設定為 1， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&12;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>CReBarCtrl::SetBandInfo  
 實作的 Win32 訊息的行為[RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 接收新設定的群組列的以零為起始索引。  
  
 `prbbi`  
 指標[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)結構，定義要插入列。 您必須設定`cbSize`此結構的成員`sizeof(REBARBANDINFO)`傳送此訊息之前。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&13;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>CReBarCtrl::SetBandWidth  
 在目前的 rebar 控制項中設定指定固定的寬度。  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `uBand`|Rebar 群組列的以零為起始的索引。|  
|[in] `cxWidth`|新的 rebar 群組列，單位為像素的寬度。|  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 `true`，否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_rebar`，也就是用來存取目前的 rebar 控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定每個 rebar 是相同的寬度。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>CReBarCtrl::SetBarInfo  
 實作的 Win32 訊息的行為[RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>參數  
 `prbi`  
 指標[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)結構，其中包含要設定的資訊。 您必須設定`cbSize`此結構的成員`sizeof(REBARINFO)`傳送此訊息之前  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&14;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>CReBarCtrl::SetBkColor  
 實作的 Win32 訊息的行為[RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 `clr`  
 **COLORREF**值，表示新的預設背景色彩。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，表示先前的預設背景色彩。  
  
### <a name="remarks"></a>備註  
 請參閱本主題，如需有關何時要設定背景色彩，以及如何設定預設值。  
  
##  <a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme  
 Rebar 控制項上設定按鈕的色彩配置。  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>參數  
 `lpcs`  
 指標[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 **新增的色彩配置**結構包含按鈕醒目提示色彩和陰影色彩。  
  
##  <a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle  
 設定目前的 rebar 控制項的延伸的樣式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwMask,   
    DWORD dwStyleEx);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwMask`|位元組合 (OR) 旗標，指定的旗標在`dwStyleEx`參數套用。 使用一或多個下列值︰<br /><br /> RBS_EX_SPLITTER︰ 根據預設，顯示分隔器下方水平的模式，並向在垂直模式中。<br /><br /> RBS_EX_TRANSPARENT︰ 轉送[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)給父視窗的訊息。|  
|[in] `dwStyleEx`|位元組合 (OR) 旗標，指定要套用樣式。 若要設定樣式，指定相同的旗標，用於`dwMask`參數。 若要重設樣式，請指定二進位的零。|  
  
### <a name="return-value"></a>傳回值  
 上一個延伸樣式。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setimagelist"></a>CReBarCtrl::SetImageList  
 將影像清單指派給 rebar 控制項。  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，其中包含指派給 rebar 控制項的影像清單。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="setowner"></a>CReBarCtrl::SetOwner  
 實作的 Win32 訊息的行為[RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指標`CWnd`設為 rebar 控制項的擁有者的物件。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md) rebar 控制項的目前擁有者的物件。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式會使用指標`CWnd`rebar 控制項的目前和所選擁有的物件，而不是 windows 的控制代碼。  
  
> [!NOTE]
>  此成員函式不會變更實際建立控制項; 時所設定的父代而是它會傳送通知訊息至您指定的視窗。  
  
##  <a name="setpalette"></a>CReBarCtrl::SetPalette  
 實作的 Win32 訊息的行為[RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>參數  
 *hPal*  
 `HPALETTE` ，指定新的 rebar 控制項將使用的調色盤。  
  
### <a name="return-value"></a>傳回值  
 指標[CPalette](../../mfc/reference/cpalette-class.md)物件，指定 rebar 控制項的前一個調色盤。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式使用`CPalette`物件做為其傳回值，而不要用`HPALETTE`。  
  
##  <a name="settextcolor"></a>CReBarCtrl::SetTextColor  
 實作的 Win32 訊息的行為[RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 `clr`  
 A **COLORREF**中的值，表示新的文字色彩`CReBarCtrl`物件。  
  
### <a name="return-value"></a>傳回值  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)與相關聯的值，表示前一個文字色彩`CReBarCtrl`物件。  
  
### <a name="remarks"></a>備註  
 它可支援 rebar 控制項中的文字色彩的彈性。  
  
##  <a name="settooltips"></a>CReBarCtrl::SetToolTips  
 將工具提示控制項與 rebar 控制項產生關聯。  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>參數  
 *pToolTip*  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件  
  
### <a name="remarks"></a>備註  
 您必須銷毀`CToolTipCtrl`物件時用完。  
  
##  <a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme  
 設定 rebar 控制項的視覺化樣式。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>參數  
 `pszSubAppName`  
 包含要設定之 rebar 視覺化樣式的 Unicode 字串指標。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="showband"></a>CReBarCtrl::ShowBand  
 實作的 Win32 訊息的行為[RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `uBand`  
 在 rebar 控制項群組列的以零起始的索引。  
  
 *fShow*  
 如果應該顯示或隱藏群組列表示。 如果這個值是**TRUE**，將會顯示寬。 否則，將會隱藏群組列。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="sizetorect"></a>CReBarCtrl::SizeToRect  
 實作的 Win32 訊息的行為[RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `rect`  
 參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定 rebar 控制項應該調整大小的矩形。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式使用`CRect`物件做為參數，而非`RECT`結構。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



