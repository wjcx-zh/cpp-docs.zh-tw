---
title: CSliderCtrl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c26df378c500b8c1384f7a357b93693b215ca10
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079612"
---
# <a name="csliderctrl-class"></a>CSliderCtrl 類別
提供 Windows 通用滑桿控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|建構 `CSliderCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|清除目前的選取範圍中的滑桿控制項。|  
|[CSliderCtrl::ClearTics](#cleartics)|移除滑桿控制項的目前刻度標記。|  
|[CSliderCtrl::Create](#create)|建立滑桿控制項，並將它附加至`CSliderCtrl`物件。|  
|[CSliderCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立的滑桿控制項，並將它附加至`CSliderCtrl`物件。|  
|[CSliderCtrl::GetBuddy](#getbuddy)|擷取在指定位置的滑桿控制項協同視窗的控制代碼。|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|擷取通道的滑桿控制項的大小。|  
|[CSliderCtrl::GetLineSize](#getlinesize)|擷取線條的大小滑桿控制項。|  
|[CSliderCtrl::GetNumTics](#getnumtics)|擷取滑桿控制項中的刻度數目。|  
|[CSliderCtrl::GetPageSize](#getpagesize)|擷取滑桿控制項的頁面大小。|  
|[CSliderCtrl::GetPos](#getpos)|擷取目前的滑桿的位置。|  
|[CSliderCtrl::GetRange](#getrange)|擷取滑桿的最小和最大位置。|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|擷取滑桿的最大位置。|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|擷取滑桿的最小位置。|  
|[CSliderCtrl::GetSelection](#getselection)|擷取目前的選取範圍的範圍。|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|擷取目前 trackbar 控制項中的滑桿的長度。|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|擷取滑桿控制項的捲動方塊的大小。|  
|[CSliderCtrl::GetTic](#gettic)|擷取指定的刻度的位置。|  
|[CSliderCtrl::GetTicArray](#getticarray)|擷取滑桿控制項刻度標記位置陣列。|  
|[CSliderCtrl::GetTicPos](#getticpos)|擷取用戶端座標中指定的刻度的位置。|  
|[CSliderCtrl::GetToolTips](#gettooltips)|如果有的話，請擷取指派至滑桿控制項，工具提示控制項的控制代碼。|  
|[CSliderCtrl::SetBuddy](#setbuddy)|將視窗指派為滑桿控制項的協同視窗。|  
|[CSliderCtrl::SetLineSize](#setlinesize)|設定線條的大小滑桿控制項。|  
|[CSliderCtrl::SetPageSize](#setpagesize)|設定滑桿控制項的頁面大小。|  
|[CSliderCtrl::SetPos](#setpos)|設定目前滑桿的位置。|  
|[CSliderCtrl::SetRange](#setrange)|設定滑桿的最小和最大位置。|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|設定最大滑桿的位置。|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|設定滑桿的最小位置。|  
|[CSliderCtrl::SetSelection](#setselection)|設定目前選取範圍的範圍。|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|設定目前 trackbar 控制項中的滑桿的長度。|  
|[CSliderCtrl::SetTic](#settic)|設定指定的刻度的位置。|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|每個滑桿控制項遞增值的標記設定刻度的頻率。|  
|[CSliderCtrl::SetTipSide](#settipside)|Trackbar 控制項位置的工具提示控制項使用。|  
|[CSliderCtrl::SetToolTips](#settooltips)|將工具提示控制項指派給滑桿控制項。|  
  
## <a name="remarks"></a>備註  
 「 滑桿控制項 」 (也稱為 trackbar) 會包含滑桿和選擇性刻度標記的視窗。 使用者移動滑桿，使用滑鼠或方向鍵時，控制項會傳送通知訊息，以指出變更。  
  
 當您想要使用者選取一個不連續的值或一組範圍內的連續值時，滑桿控制項就很有用。 例如，您可以使用滑桿控制項允許使用者透過移動滑桿至指定的刻度標記，設定鍵盤的重複率。  
  
 這個控制項 (因此`CSliderCtrl`類別) 僅適用於 Windows 95/98、 Windows NT 的版本 3.51 下執行的程式和更新版本。  
  
 您在建立時指定的增量，滑桿移動。 例如，如果您指定滑桿移應有五個範圍，滑桿只能佔用六個位置： 一個位置是在左邊的滑桿控制項和範圍中的之每個增量，一個位置。 一般來說，這些位置的每一個都以刻度標記來識別。  
  
 使用建構函式建立滑桿和`Create`成員函式`CSliderCtrl`。 當您建立的滑桿控制項之後時，您可以使用成員函式中的`CSliderCtrl`變更許多屬性。 您可以進行的變更包括設定滑桿的最小和最大位置、繪製刻度標記、設定選取範圍，以及重新調整滑桿定位。  
  
 如需有關使用`CSliderCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="clearsel"></a>  CSliderCtrl::ClearSel  
 清除目前的選取範圍中的滑桿控制項。  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *bRedraw*  
 重繪旗標。 如果這個參數是**TRUE**，滑桿會重新繪製之後會清除選取範圍, 否則滑桿不重新繪製。  
  
##  <a name="cleartics"></a>  CSliderCtrl::ClearTics  
 移除滑桿控制項的目前刻度標記。  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *bRedraw*  
 重繪旗標。 如果這個參數是**TRUE**，滑桿會重新繪製之後會清除刻度標記, 否則滑桿不重新繪製。  
  
##  <a name="create"></a>  CSliderCtrl::Create  
 建立滑桿控制項，並將它附加至`CSliderCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *dwStyle*  
 指定滑桿控制項的樣式。 套用的任何組合[滑桿控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中所述，在 Windows SDK 中，加入控制項。  
  
 *rect*  
 指定滑桿控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 *pParentWnd*  
 指定滑桿控制項的父視窗，通常`CDialog`。 它不得為**NULL**。  
  
 *nID*  
 指定滑桿控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 您建構`CSliderCtrl`分成兩個步驟。 首先，呼叫建構函式，然後再呼叫`Create`，建立滑桿控制項，並將它附加至`CSliderCtrl`物件。  
  
 為設定的值根據`dwStyle`，滑桿控制項可以具有垂直或水平方向。 它可以有刻度任一邊側邊，或兩者皆非。 它也可以用來指定連續值的範圍。  
  
 若要將延伸的視窗樣式套用至滑桿控制項，呼叫[CreateEx](#createex)而不是`Create`。  
  
##  <a name="createex"></a>  CSliderCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CSliderCtrl`物件。  
  
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
 指定正在建立的控制項的延伸的樣式。 如需延伸的視窗樣式的清單，請參閱*dwExStyle*參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 *dwStyle*  
 指定滑桿控制項的樣式。 套用的任何組合[滑桿控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中所述，在 Windows SDK 中，加入控制項。  
  
 *rect*  
 若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立，用戶端座標中之視窗*pParentWnd*。  
  
 *pParentWnd*  
 為控制項的父視窗的指標。  
  
 *nID*  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，由 Windows 擴充的樣式序言**WS_EX_**。  
  
##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl  
 建構 `CSliderCtrl` 物件。  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy  
 擷取在指定位置的滑桿控制項協同視窗的控制代碼。  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 *fLocation*  
 布林值，指出這兩個擷取的協同視窗控制代碼。 可為下列其中一個值：  
  
- **TRUE**擷取左邊的滑桿好友的控制代碼。 如果滑桿控制項使用`TBS_VERT`樣式，訊息將會擷取滑桿上方朋友。  
  
- **FALSE**擷取右邊的滑桿好友的控制代碼。 如果滑桿控制項使用`TBS_VERT`樣式，訊息將會擷取下方的滑桿朋友。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)協同視窗指定位置的物件`fLocation`，或**NULL**如果沒有協同視窗存在於該位置。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178)、 Windows SDK 中所述。 如需滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect  
 擷取的大小和位置，這個周框滑桿控制項的通道。  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>參數  
 *lprc*  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)函式會傳回物件，其中包含的大小和位置的通道之周框。  
  
### <a name="remarks"></a>備註  
 通道是透過將滑桿移，且已選取範圍時將會包含反白顯示的區域。  
  
##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize  
 擷取滑桿控制項之線條的大小。  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 線滑桿控制項的大小。  
  
### <a name="remarks"></a>備註  
 線條大小會影響多少，滑桿移動的**TB_LINEUP**和**TB_LINEDOWN**通知。 線條大小的預設值為 1。  
  
##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics  
 擷取滑桿控制項中的刻度數目。  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項中的刻度數。  
  
##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize  
 擷取滑桿控制項的頁面大小。  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項的頁面大小。  
  
### <a name="remarks"></a>備註  
 頁面大小會影響多少，滑桿移動的**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="getpos"></a>  CSliderCtrl::GetPos  
 擷取滑桿的滑桿控制項中目前的位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前位置。  
  
##  <a name="getrange"></a>  CSliderCtrl::GetRange  
 擷取滑桿控制項在滑桿的最大和最小位置。  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>參數  
 *nMin*  
 整數，接收的最小位置參考。  
  
 *nMax*  
 整數，接收的最大位置參考。  
  
### <a name="remarks"></a>備註  
 此函式將值複製到所參考的整數*nMin*和*nMax*。  
  
##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax  
 擷取滑桿控制項在滑桿的最大的位置。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項的最大的位置。  
  
##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin  
 擷取滑桿控制項在滑桿的最小的位置。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項的最小的位置。  
  
##  <a name="getselection"></a>  CSliderCtrl::GetSelection  
 擷取滑桿控制項中目前的選取範圍的開始和結束位置。  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>參數  
 *nMin*  
 接收目前選取範圍的開始位置的整數的參考。  
  
 *nMax*  
 接收目前選取範圍的結束位置的整數的參考。  
  
##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength  
 擷取目前 trackbar 控制項中的滑桿的長度。  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿，像素為單位的長度。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201) Windows SDK 中所述的訊息。  
  
##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect  
 擷取的大小和滑桿 （捲動方塊），這個周框中的滑桿控制項的位置。  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>參數  
 *lprc*  
 指標`CRect`函式傳回時包含滑桿的週框物件。  
  
##  <a name="gettic"></a>  CSliderCtrl::GetTic  
 擷取中的滑桿控制項刻度的位置。  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>參數  
 *nTic*  
 識別的刻度以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指定的刻度或-1，否則位置*nTic*未指定有效的索引。  
  
##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray  
 擷取陣列包含的刻度標記的滑桿控制項位置的位址。  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列包含滑桿控制項刻度標記位置的位址。  
  
##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos  
 擷取目前在滑桿控制項刻度的實體位置。  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>參數  
 *nTic*  
 識別的刻度以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 實體位置，用戶端座標中指定的刻度或-1，否則*nTic*未指定有效的索引。  
  
##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips  
 如果有的話，請擷取指派至滑桿控制項，工具提示控制項的控制代碼。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件，或**NULL**如果工具提示不在使用中。 如果不使用滑桿控制項**TBS_TOOLTIPS**樣式，則傳回值是**NULL**。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209)、 Windows SDK 中所述。 請注意，此成員函式傳回`CToolTipCtrl`物件而不是控制項的控制代碼。  
  
 如需滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy  
 將視窗指派為滑桿控制項的協同視窗。  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pWndBuddy*  
 指標`CWnd`會被設定為滑桿控制項的好友的物件。  
  
 *fLocation*  
 值，指定要顯示協同視窗的位置。 這個值可以是下列其中一項：  
  
- **TRUE**如果 trackbar 控制項使用，將會出現 trackbar 左邊的好友`TBS_HORZ`樣式。 如果使用 trackbar`TBS_VERT`樣式，好友上方 trackbar 控制項。  
  
- **FALSE**如果 trackbar 控制項使用，將會出現 trackbar 右邊的好友`TBS_HORZ`樣式。 如果使用 trackbar`TBS_VERT`樣式，好友出現 trackbar 控制項下方。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)先前指派給滑桿控制項，在該位置的物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213)、 Windows SDK 中所述。 請注意，此成員函式會使用指標`CWnd`物件，而不是其傳回值和參數的視窗控制代碼。  
  
 如需滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize  
 設定滑桿控制項之線條的大小。  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 *nSize*  
 滑桿控制項的新行大小。  
  
### <a name="return-value"></a>傳回值  
 先前的列大小。  
  
### <a name="remarks"></a>備註  
 線條大小會影響多少，滑桿移動的**TB_LINEUP**和**TB_LINEDOWN**通知。  
  
##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize  
 設定滑桿控制項的頁面大小。  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 *nSize*  
 滑桿控制項的新的頁面大小。  
  
### <a name="return-value"></a>傳回值  
 先前的頁面大小。  
  
### <a name="remarks"></a>備註  
 頁面大小會影響多少，滑桿移動的**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="setpos"></a>  CSliderCtrl::SetPos  
 將滑桿的目前位置設定滑桿控制項。  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>參數  
 *nPos*  
 指定新的滑桿位置。  
  
##  <a name="setrange"></a>  CSliderCtrl::SetRange  
 設定中的滑桿控制項的滑桿範圍 （最小和最大位置）。  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *nMin*  
 最小滑桿的位置。  
  
 *nMax*  
 最大滑桿的位置。  
  
 *bRedraw*  
 重繪旗標。 如果這個參數是**TRUE**，滑桿範圍設定之後會重新繪製; 否則滑桿不重新繪製。  
  
##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax  
 設定中的滑桿控制項的滑桿的最大範圍。  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *nMax*  
 最大滑桿的位置。  
  
 *bRedraw*  
 重繪旗標。 如果這個參數是**TRUE**，滑桿範圍設定之後會重新繪製; 否則滑桿不重新繪製。  
  
##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin  
 設定中的滑桿控制項的滑桿的最小的範圍。  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 *nMin*  
 最小滑桿的位置。  
  
 *bRedraw*  
 重繪旗標。 如果這個參數是**TRUE**，滑桿範圍設定之後會重新繪製; 否則滑桿不重新繪製。  
  
##  <a name="setselection"></a>  CSliderCtrl::SetSelection  
 設定目前選取範圍的開始和結束位置中的滑桿控制項。  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 *nMin*  
 滑桿的開始位置。  
  
 *nMax*  
 結束滑桿的位置。  
  
##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength  
 設定目前 trackbar 控制項中的滑桿的長度。  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in]*nLength*|滑桿，像素為單位的長度。|  
  
### <a name="remarks"></a>備註  
 此方法需要 trackbar 控制項設定為[TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147)樣式。  
  
 這個方法會傳送[TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234) Windows SDK 中所述的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數`m_sliderCtrl`，也就是用來存取目前 trackbar 控制項。 此範例也會定義變數， `thumbLength`，也就是用來儲存 trackbar 控制項的捲動方塊元件的預設長度。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定 trackbar 控制項的捲動方塊元件兩次其預設值的長度。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>  CSliderCtrl::SetTic  
 滑桿控制項中設定刻度的位置。  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>參數  
 *nTic*  
 刻度的位置。 這個參數必須指定正數值。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果設定刻度標記。否則便是 0。  
  
##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq  
 設定使用的刻度標記會顯示在滑桿的頻率。  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>參數  
 *nFreq*  
 刻度的頻率。  
  
### <a name="remarks"></a>備註  
 比方說，如果頻率設定為 2，則會顯示刻度標記的滑桿的範圍內的遞增值。 預設設定的頻率 1 （也就是每個範圍中的增量是刻度標記與相關聯）。  
  
 您必須建立與控制項`TBS_AUTOTICKS`来使用此函式樣式。 如需詳細資訊，請參閱[CSliderCtrl::Create](#create)。  
  
##  <a name="settipside"></a>  CSliderCtrl::SetTipSide  
 Trackbar 控制項位置的工具提示控制項使用。  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>參數  
 *n 位置*  
 值，表示要顯示工具提示控制項的位置。 如需可能值的清單，請參閱的 Win32 訊息[TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240)、 Windows SDK 中所述。  
  
### <a name="return-value"></a>傳回值  
 值，表示工具提示控制項的上一個位置。 傳回的值等於其中一個可能的值為*n 位置*。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為**TBM_SETTIPSIDE**、 Windows SDK 中所述。 滑桿控制項使用**TBS_TOOLTIPS**樣式顯示工具提示。 如需滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips  
 將工具提示控制項指派給滑桿控制項。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>參數  
 *pWndTip*  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件，其中包含要使用滑桿控制項的工具提示。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242)、 Windows SDK 中所述。 滑桿控制項與建立時**TBS_TOOLTIPS**樣式，它會建立預設工具提示控制項的滑桿旁，顯示目前的滑桿的位置出現。 如需滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl 類別](../../mfc/reference/cprogressctrl-class.md)
