---
title: CReBarCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ba3b93c1c45edabc86759a14f27309849d58553
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42544426"
---
# <a name="crebarctrl-class"></a>CReBarCtrl 類別
封裝 Rebar 控制項的功能，這個控制項是子視窗的容器。  
  
## <a name="syntax"></a>語法  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|建構 `CReBarCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](#begindrag)|Rebar 控制項置於拖放模式。|  
|[CReBarCtrl::Create](#create)|建立 rebar 控制項，並將它附加至`CReBarCtrl`物件。|  
|[CReBarCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立 rebar 控制項，並將它附加至`CReBarCtrl`物件。|  
|[CReBarCtrl::DeleteBand](#deleteband)|從 rebar 控制項中刪除群組列。|  
|[CReBarCtrl::DragMove](#dragmove)|更新之後呼叫的 rebar 控制項的拖曳位置`BeginDrag`。|  
|[CReBarCtrl::EndDrag](#enddrag)|Rebar 控制項的拖放作業就會終止。|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|擷取頻外的框線。|  
|[CReBarCtrl::GetBandCount](#getbandcount)|擷取群組列的 rebar 控制項中目前的計數。|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|擷取指定的群組列的 rebar 控制項中的相關資訊。|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|擷取頻外的邊界。|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|擷取 rebar 控制項的高度。|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|擷取 rebar 控制項和它所使用的影像清單的相關資訊。|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|擷取 rebar 控制項的預設背景色彩。|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|擷取[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)rebar 控制項相關聯的結構。|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|擷取 rebar 控制項的`IDropTarget`介面指標。|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|取得目前的 rebar 控制項的延伸的樣式。|  
|[CReBarCtrl::GetImageList](#getimagelist)|擷取映像相關聯的清單與 rebar 控制項。|  
|[CReBarCtrl::GetPalette](#getpalette)|擷取目前的 rebar 控制項的調色盤。|  
|[CReBarCtrl::GetRect](#getrect)|擷取給定的頻外，rebar 控制項中指定的週框。|  
|[CReBarCtrl::GetRowCount](#getrowcount)|擷取 rebar 控制項中的頻外資料列的數目。|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|擷取指定的資料列的 rebar 控制項的高度。|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|擷取 rebar 控制項的預設文字色彩。|  
|[CReBarCtrl::GetToolTips](#gettooltips)|擷取與 rebar 控制項相關聯的任何工具提示控制項的控制代碼。|  
|[CReBarCtrl::HitTest](#hittest)|判斷哪一部分 rebar 群組列在指定的時間點，在畫面上，如果此時 rebar 群組列存在。|  
|[CReBarCtrl::IDToIndex](#idtoindex)|Rebar 控制項中的頻外索引會將群組列識別碼 (ID)。|  
|[Crebarctrl:: Insertband](#insertband)|Rebar 控制項中插入新的群組列。|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|調整成最大大小的 rebar 控制項中的頻外的大小。|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|調整成最小大小 rebar 控制項中的頻外的大小。|  
|[CReBarCtrl::MoveBand](#moveband)|將群組列從一個索引移到另一個。|  
|[CReBarCtrl::PushChevron](#pushchevron)|以程式設計方式將推入的 > 形箭號。|  
|[CReBarCtrl::RestoreBand](#restoreband)|調整至其理想大小的 rebar 控制項中的頻外的大小。|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Rebar 控制項中設定現有的頻外的特性。|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|設定目前的 rebar 控制項中的指定停駐的寬線的寬度。|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|設定 rebar 控制項的特性。|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|設定 rebar 控制項的預設背景色彩。|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Rebar 控制項上設定按鈕的色彩配置。|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|設定目前的 rebar 控制項的延伸的樣式。|  
|[CReBarCtrl::SetImageList](#setimagelist)|設定 rebar 控制項的影像清單。|  
|[CReBarCtrl::SetOwner](#setowner)|設定 rebar 控制項的主控視窗。|  
|[CReBarCtrl::SetPalette](#setpalette)|設定目前的 rebar 控制項的調色盤。|  
|[CReBarCtrl::SetTextColor](#settextcolor)|設定 rebar 控制項的預設文字色彩。|  
|[CReBarCtrl::SetToolTips](#settooltips)|關聯 rebar 控制項中的工具提示控制項。|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|設定 rebar 控制項的視覺化樣式。|  
|[CReBarCtrl::ShowBand](#showband)|顯示或隱藏指定的頻外，rebar 控制項中。|  
|[CReBarCtrl::SizeToRect](#sizetorect)|符合指定的矩形的 rebar 控制項。|  
  
## <a name="remarks"></a>備註  
 Rebar 控制項所在的應用程式會指派給 rebar 群組列的 rebar 控制項所包含的子視窗。 子視窗是通常是另一個常見的控制項。  
  
 Rebar 控制項包含一或多個群組列。 每個群組列可以包含移駐夾列、 點陣圖、 文字標籤和子視窗的組合。 群組列可以包含的每一個項目其中之一。  
  
 Rebar 控制項可以顯示子視窗，透過指定的背景點陣圖。 所有的 rebar 控制項可以調整大小，除了使用 RBBS_FIXEDSIZE 樣式。 當您重新調整位置，或調整 rebar 控制項的大小，rebar 控制項管理的大小和位置指派給該群組列的子視窗。 若要調整大小或變更在控制項內群組列的順序，按一下並拖曳群組列的移駐夾列。  
  
 下圖顯示具有三個群組列的 rebar 控制項：  
  
-   群組列 0 包含一般、 透明工具列控制項。  
  
-   頻外 1 包含這兩個透明的標準和透明下拉式按鈕。  
  
-   頻外 2 包含下拉式方塊和四個標準按鈕。  
  
     ![Rebar 功能表範例](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Rebar 控制項  
 Rebar 控制項支援：  
  
-   影像清單。  
  
-   訊息處理。  
  
-   自訂繪製功能。  
  
-   各種不同的控制項的樣式，除了標準的視窗樣式。 如需這些樣式的清單，請參閱 < [Rebar 控制項的樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 中。  
  
 如需詳細資訊，請參閱 <<c0> [ 使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag  
 實作 Win32 訊息的行為[RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429)、 Windows SDK 中所述。  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 拖放作業會影響此群組列的以零為起始的索引。  
  
 *dwPos*  
 DWORD 值，包含開始滑鼠座標。 水平座標包含在取代 LOWORD 而垂直座標包含在 HIWORD。 如果您傳遞 (DWORD)-1，rebar 控制項將使用上一次呼叫控制項的執行緒，滑鼠位置`GetMessage`或`PeekMessage`。  
  
##  <a name="create"></a>  CReBarCtrl::Create  
 建立 rebar 控制項，並將它附加至`CReBarCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定 rebar 控制項的樣式套用至控制項的組合。 請參閱[Rebar 控制項的樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK，如需支援的樣式的清單中。  
  
 *rect*  
 參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，也就是位置和 rebar 控制項的大小。  
  
 *pParentWnd*  
 指標[CWnd](../../mfc/reference/cwnd-class.md) rebar 控制項的父視窗物件。 它必須不是 NULL。  
  
 *nID*  
 指定 rebar 控制項的控制項 id。  
  
### <a name="return-value"></a>傳回值  
 如果物件已成功; 建立為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 建立 rebar 控制項中兩個步驟：  
  
1.  呼叫[CReBarCtrl](#crebarctrl)建構`CReBarCtrl`物件。  
  
2.  呼叫此成員函式，會建立 Windows rebar 控制項，並將它附加至`CReBarCtrl`物件。  
  
 當您呼叫`Create`，常見的控制項都已初始化。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CReBarCtrl::CreateEx  
 建立控制項 （子視窗），並將它與關聯`CReBarCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *dwExStyle*  
 指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 *cheaderctrl:: Create*  
 指定 rebar 控制項的樣式套用至控制項的組合。 如需支援的樣式清單，請參閱 < [Rebar 控制項的樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 中。  
  
 *rect*  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。  
  
 *pParentWnd*  
 是控制項的父視窗的指標。  
  
 *nID*  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。  
  
##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl  
 建立 `CReBarCtrl` 物件。  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>範例  
  範例，請參閱[CReBarCtrl::Create](#create)。  
  
##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand  
 實作 Win32 訊息的行為[RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431)、 Windows SDK 中所述。  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 要刪除的群組列的以零為起始索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，刪除頻外，非零值。否則為零。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>  CReBarCtrl::DragMove  
 實作 Win32 訊息的行為[RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove)、 Windows SDK 中所述。  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>參數  
 *dwPos*  
 包含新的滑鼠座標的 DWORD 值。 水平座標包含在取代 LOWORD 而垂直座標包含在 HIWORD。 如果您傳遞 (DWORD)-1，rebar 控制項將使用上一次呼叫控制項的執行緒，滑鼠位置`GetMessage`或`PeekMessage`。  
  
##  <a name="enddrag"></a>  CReBarCtrl::EndDrag  
 實作 Win32 訊息的行為[RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435)、 Windows SDK 中所述。  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders  
 實作 Win32 訊息的行為[RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437)、 Windows SDK 中所述。  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 框線將擷取群組列的以零為起始索引。  
  
 *中華人民共和國*  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構將會接收頻外框線。 如果 rebar 控制項有 RBS_BANDBORDERS 樣式，這個結構的每個成員會收到的像素數，一端對應的頻外，構成框線。 如果 rebar 控制項並沒有 RBS_BANDBORDERS 樣式，這個結構的左的成員會收到有效的資訊。 如需 rebar 控制項的樣式的描述，請參閱 < [Rebar 控制項的樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 中。  
  
##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount  
 實作 Win32 訊息的行為[RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439)、 Windows SDK 中所述。  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指派給控制項的群組列的數目。  
  
##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo  
 實作 Win32 訊息的行為[RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451) Windows SDK 中所述。  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 將擷取資訊的群組列的以零起始索引。  
  
 *prbbi*  
 指標[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)接收頻外資訊的結構。 您必須設定`cbSize`此結構的成員`sizeof(REBARBANDINFO)`並設定`fMask`您想要傳送此訊息之前，先擷取之項目的成員。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins  
 擷取頻外的邊界。  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>參數  
 *pMargins*  
 指標[邊界](http://msdn.microsoft.com/library/windows/desktop/bb773244)接收資訊的結構。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬[RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453)訊息、 Windows SDK 中所述。  
  
##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight  
 擷取 rebar 列的高度。  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示高度，單位為像素的控制項。  
  
##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo  
 實作 Win32 訊息的行為[RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457)、 Windows SDK 中所述。  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>參數  
 *prbi*  
 指標[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)將會收到 rebar 控制項資訊的結構。 您必須設定*cbSize*屬於此結構`sizeof(REBARINFO)`之前先傳送此訊息。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor  
 實作 Win32 訊息的行為[RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459)、 Windows SDK 中所述。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 COLORREF 值，這個值表示目前的預設背景色彩。  
  
##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme  
 擷取[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)rebar 控制項的結構。  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>參數  
 *lpc*  
 指標[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)結構，在 Windows SDK 中所述。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 `COLORSCHEME`結構包含按鈕反白顯示色彩和按鈕的陰影色彩。  
  
##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget  
 實作 Win32 訊息的行為[RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463)、 Windows SDK 中所述。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)介面。  
  
##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle  
 取得目前的 rebar 控制項的延伸的樣式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位元組合 (OR) 旗標，表示延伸的樣式。 可能的旗標為 RBS_EX_SPLITTER 和 RBS_EX_TRANSPARENT。 如需詳細資訊，請參閱 < *dwMask*的參數[CReBarCtrl::SetExtendedStyle](#setextendedstyle)方法。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433)訊息，Windows SDK 中所述。  
  
##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList  
 取得`CImageList`rebar 控制項相關聯的物件。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件。 如果沒有映像清單設定控制項，則傳回 NULL。  
  
### <a name="remarks"></a>備註  
 此成員函式會使用的大小和遮罩中所儲存的資訊[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)結構，在 Windows SDK 中所述。  
  
##  <a name="getpalette"></a>  CReBarCtrl::GetPalette  
 擷取目前的 rebar 控制項的調色盤。  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CPalette](../../mfc/reference/cpalette-class.md)物件，指定目前的 rebar 控制項的調色盤。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式會使用`CPalette`物件做為其傳回值，而不是 HPALETTE。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>  CReBarCtrl::GetRect  
 實作 Win32 訊息的行為[RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469)、 Windows SDK 中所述。  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 在 rebar 控制項寬線的以零為起始索引。  
  
 *中華人民共和國*  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，將會收到 rebar 群組列的界限。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount  
 實作 Win32 訊息的行為[RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471)、 Windows SDK 中所述。  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 UINT 值，表示控制項中的頻外資料列數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight  
 實作 Win32 訊息的行為[RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473)、 Windows SDK 中所述。  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>參數  
 *uRow*  
 將已擷取其高度的寬線的以零起始的索引。  
  
### <a name="return-value"></a>傳回值  
 UINT 值，表示資料列高度，單位為像素。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor  
 實作 Win32 訊息的行為[RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475)、 Windows SDK 中所述。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 COLORREF 值，這個值表示目前的預設文字色彩。  
  
##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips  
 實作 Win32 訊息的行為[RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477)、 Windows SDK 中所述。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件。  
  
### <a name="remarks"></a>備註  
 請注意，MFC 實作`GetToolTips`將指標傳回至`CToolTipCtrl`，而不是 HWND。  
  
##  <a name="hittest"></a>  CReBarCtrl::HitTest  
 實作 Win32 訊息的行為[RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494)、 Windows SDK 中所述。  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>參數  
 *prbht*  
 指標[RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391)結構。 傳送訊息之前，先`pt`這個結構的成員必須先初始化才能將測試，在工作區座標的點。  
  
### <a name="return-value"></a>傳回值  
 在指定的點或-1 之處沒有 rebar 群組列是否群組列的以零起始的索引。  
  
##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex  
 實作 Win32 訊息的行為[RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496)、 Windows SDK 中所述。  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>參數  
 *uBandID*  
 指定的頻外，應用程式定義識別碼傳入`wID`隸屬[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)結構插入群組列時。  
  
### <a name="return-value"></a>傳回值  
 以零為起始的頻外索引，如果成功，則為-1 則。 如果存在重複的群組列索引，則會傳回第一個。  
  
##  <a name="insertband"></a>  Crebarctrl:: Insertband  
 實作 Win32 訊息的行為[RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498)、 Windows SDK 中所述。  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>參數  
 *uIndex*  
 要插入的頻外的位置以零為起始的索引。 如果您將此參數設為-1 時，控制項就會將新的頻外的最後一個位置。  
  
 *prbbi*  
 指標[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)結構，定義要插入此群組列。 您必須設定*cbSize*屬於此結構`sizeof(REBARBANDINFO)`之前呼叫這個函式。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>  CReBarCtrl::MaximizeBand  
 調整成最大大小的 rebar 控制項中的頻外的大小。  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 要最大化群組列的以零為起始索引。  
  
### <a name="remarks"></a>備註  
 實作 Win32 訊息的行為[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)使用`fIdeal`設為 0，在 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>  CReBarCtrl::MinimizeBand  
 調整成最小大小 rebar 控制項中的頻外的大小。  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 若要最小化群組列的以零起始索引。  
  
### <a name="remarks"></a>備註  
 實作 Win32 訊息的行為[RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502)、 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>  CReBarCtrl::MoveBand  
 實作 Win32 訊息的行為[RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504)、 Windows SDK 中所述。  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>參數  
 *uFrom*  
 要移動的群組列的以零起始索引。  
  
 *uTo*  
 新的頻外位置以零為起始索引。 此參數值必須永遠不會大於減一的群組列的數目。 若要取得群組列的數目，請呼叫[GetBandCount](#getbandcount)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron  
 實作 Win32 訊息的行為[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506)、 Windows SDK 中所述。  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 以零為起始的 > 形箭號是推送的寬線的索引。  
  
 *lAppValue*  
 應用程式定義的 32 位元值。 請參閱*lAppValue*中[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506) Windows SDK 中。  
  
##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand  
 調整至其理想大小的 rebar 控制項中的頻外的大小。  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 要最大化群組列的以零為起始索引。  
  
### <a name="remarks"></a>備註  
 實作 Win32 訊息的行為[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)使用`fIdeal`設為 1，在 Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo  
 實作 Win32 訊息的行為[RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508)、 Windows SDK 中所述。  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 接收新的設定群組列的以零起始索引。  
  
 *prbbi*  
 指標[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)結構，定義要插入此群組列。 您必須設定`cbSize`屬於此結構`sizeof(REBARBANDINFO)`之前先傳送此訊息。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth  
 設定目前的 rebar 控制項中的指定停駐的寬線的寬度。  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*uBand*|Rebar 群組列的以零為起始的索引。|  
|[in]*cxWidth*|新的 rebar 群組列中，單位為像素的寬度。|  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511)訊息，Windows SDK 中所述。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_rebar`，也就是用來存取目前的 rebar 控制項。 下一個範例中會使用此變數。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定為相同的寬度的每個 rebar 群組列。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo  
 實作 Win32 訊息的行為[RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513)、 Windows SDK 中所述。  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>參數  
 *prbi*  
 指標[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)結構，其中包含要設定的資訊。 您必須設定`cbSize`屬於此結構`sizeof(REBARINFO)`傳送此訊息之前  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor  
 實作 Win32 訊息的行為[RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515)、 Windows SDK 中所述。  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 *clr*  
 COLORREF 值，表示新的預設背景色彩。  
  
### <a name="return-value"></a>傳回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，表示先前的預設背景色彩。  
  
### <a name="remarks"></a>備註  
 請參閱本主題，如需有關何時要設定背景色彩，以及如何設定預設值。  
  
##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme  
 Rebar 控制項上設定按鈕的色彩配置。  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>參數  
 *lpc*  
 指標[新增的色彩配置](http://msdn.microsoft.com/library/windows/desktop/bb775502)結構，在 Windows SDK 中所述。  
  
### <a name="remarks"></a>備註  
 `COLORSCHEME`結構包含按鈕反白顯示色彩和按鈕的陰影色彩。  
  
##  <a name="setextendedstyle"></a>  CReBarCtrl::SetExtendedStyle  
 設定目前的 rebar 控制項的延伸的樣式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwMask,   
    DWORD dwStyleEx);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*dwMask*|位元組合 (OR) 旗標，指定在的旗標*dwStyleEx*參數套用。 使用一或多個下列值：<br /><br /> RBS_EX_SPLITTER： 根據預設，顯示分隔器下方在水平模式中，和右邊垂直的模式。<br /><br /> RBS_EX_TRANSPARENT： 轉寄[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)父視窗的訊息。|  
|[in]*dwStyleEx*|位元組合 (OR) 旗標，指定要套用的樣式。 若要設定樣式，指定會在相同的旗標*dwMask*參數。 若要重設的樣式，請指定二進位零。|  
  
### <a name="return-value"></a>傳回值  
 先前的延伸的樣式。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519)訊息，Windows SDK 中所述。  
  
##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList  
 給 rebar 控制項中的影像清單。  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 *pImageList*  
 指標[CImageList](../../mfc/reference/cimagelist-class.md)物件，其中包含要指派給 rebar 控制項之影像清單。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
##  <a name="setowner"></a>  CReBarCtrl::SetOwner  
 實作 Win32 訊息的行為[RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522)、 Windows SDK 中所述。  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 指標`CWnd`設為 rebar 控制項的擁有者的物件。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md) rebar 控制項的目前擁有者的物件。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式會使用指標`CWnd`這兩個目前與所選取擁有者的 rebar 控制項物件，而不是控制代碼對應到 windows。  
  
> [!NOTE]
>  此成員函式不會變更實際的父代時建立控制項; 所設定而是它會通知訊息傳送至您指定的視窗。  
  
##  <a name="setpalette"></a>  CReBarCtrl::SetPalette  
 實作 Win32 訊息的行為[RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520)、 Windows SDK 中所述。  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>參數  
 *hPal*  
 指定新 rebar 控制項將使用的調色盤 HPALETTE。  
  
### <a name="return-value"></a>傳回值  
 指標[CPalette](../../mfc/reference/cpalette-class.md)物件，指定 rebar 控制項的前一個調色盤。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式會使用`CPalette`物件做為其傳回值，而不是 HPALETTE。  
  
##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor  
 實作 Win32 訊息的行為[RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524)、 Windows SDK 中所述。  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 *clr*  
 COLORREF 值，表示新的文字色彩`CReBarCtrl`物件。  
  
### <a name="return-value"></a>傳回值  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)與相關聯的值，表示先前的文字色彩`CReBarCtrl`物件。  
  
### <a name="remarks"></a>備註  
 它被提供來支援 rebar 控制項中的文字色彩的彈性。  
  
##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips  
 將工具提示控制項與 rebar 控制項產生關聯。  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>參數  
 *pToolTip*  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件  
  
### <a name="remarks"></a>備註  
 您必須銷毀`CToolTipCtrl`物件時完成它。  
  
##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme  
 設定 rebar 控制項的視覺化樣式。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>參數  
 *pszSubAppName*  
 包含 rebar 視覺化樣式，若要設定的 Unicode 字串指標。  
  
### <a name="return-value"></a>傳回值  
 不會使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式會模擬[RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530)訊息、 Windows SDK 中所述。  
  
##  <a name="showband"></a>  CReBarCtrl::ShowBand  
 實作 Win32 訊息的行為[RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532)、 Windows SDK 中所述。  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *uBand*  
 在 rebar 控制項寬線的以零為起始索引。  
  
 *fShow*  
 指出是否群組列應該要顯示或隱藏。 如果此值為 TRUE，就會顯示此群組列。 否則，群組列將會隱藏。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect  
 實作 Win32 訊息的行為[RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534)、 Windows SDK 中所述。  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 *rect*  
 參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，指定應該調整大小的 rebar 控制項的矩形。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 請注意，此成員函式會使用`CRect`物件做為參數，而非`RECT`結構。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


