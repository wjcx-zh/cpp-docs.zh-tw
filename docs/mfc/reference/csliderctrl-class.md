---
title: "CSliderCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- Windows common controls [C++], CSliderCtrl
- slider controls, CSliderCtrl class
- CSliderCtrl class, common controls
- CSliderCtrl class
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 22
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
ms.openlocfilehash: 0d024c7d6670ff3b7a94b9657151e7bf1958d5f1
ms.lasthandoff: 02/24/2017

---
# <a name="csliderctrl-class"></a>CSliderCtrl 類別
提供 Windows 通用滑桿控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|建構 `CSliderCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|清除目前的選取範圍中的滑桿控制項。|  
|[CSliderCtrl::ClearTics](#cleartics)|滑桿控制項，會移除目前的刻度標記。|  
|[CSliderCtrl::Create](#create)|建立滑桿控制項，並將它附加`CSliderCtrl`物件。|  
|[CSliderCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立滑桿控制項，並附加至該`CSliderCtrl`物件。|  
|[CSliderCtrl::GetBuddy](#getbuddy)|擷取在指定位置的滑桿控制項協同視窗的控制代碼。|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|擷取通道滑桿控制項的大小。|  
|[CSliderCtrl::GetLineSize](#getlinesize)|擷取滑桿控制項的線條大小。|  
|[CSliderCtrl::GetNumTics](#getnumtics)|擷取滑桿控制項中的刻度數。|  
|[CSliderCtrl::GetPageSize](#getpagesize)|擷取滑桿控制項的頁面大小。|  
|[CSliderCtrl::GetPos](#getpos)|擷取目前的滑桿的位置。|  
|[CSliderCtrl::GetRange](#getrange)|擷取有個滑桿的最小和最大位置。|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|擷取有個滑桿的最大位置。|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|擷取有個滑桿的最小位置。|  
|[CSliderCtrl::GetSelection](#getselection)|擷取目前的選取範圍的範圍。|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|擷取目前 trackbar 控制項中的滑桿的長度。|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|擷取滑桿控制項的捲動方塊的大小。|  
|[CSliderCtrl::GetTic](#gettic)|擷取指定的刻度的位置。|  
|[CSliderCtrl::GetTicArray](#getticarray)|擷取滑桿控制項的刻度標記位置的陣列。|  
|[CSliderCtrl::GetTicPos](#getticpos)|擷取用戶端座標中指定的刻度的位置。|  
|[CSliderCtrl::GetToolTips](#gettooltips)|如果有的話，請擷取指派給控制項的滑桿，工具提示控制項的控制代碼。|  
|[CSliderCtrl::SetBuddy](#setbuddy)|將視窗指派為協同視窗的滑桿控制項。|  
|[CSliderCtrl::SetLineSize](#setlinesize)|設定滑桿控制項的線條大小。|  
|[CSliderCtrl::SetPageSize](#setpagesize)|設定滑桿控制項的頁面大小。|  
|[CSliderCtrl::SetPos](#setpos)|設定目前滑桿的位置。|  
|[CSliderCtrl::SetRange](#setrange)|設定有個滑桿的最小和最大位置。|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|設定最大滑桿的位置。|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|設定有個滑桿的最小位置。|  
|[CSliderCtrl::SetSelection](#setselection)|設定目前選取的範圍。|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|設定目前 trackbar 控制項中的滑桿的長度。|  
|[CSliderCtrl::SetTic](#settic)|設定指定的刻度的位置。|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|設定刻度的頻率標記每個滑桿控制項遞增。|  
|[CSliderCtrl::SetTipSide](#settipside)|Trackbar 控制項位置的工具提示控制項使用。|  
|[CSliderCtrl::SetToolTips](#settooltips)|將工具提示控制項指派給滑桿控制項。|  
  
## <a name="remarks"></a>備註  
 「 滑桿控制項 」 (也稱為 trackbar) 是包含有個滑桿和選擇性刻度標記的視窗。 當使用者移動滑桿，使用滑鼠或方向鍵時，控制項就會傳送通知訊息，以指出變更。  
  
 當您想要使用者選取一個不連續的值或一組範圍內的連續值時，滑桿控制項就很有用。 例如，您可以使用滑桿控制項允許使用者透過移動滑桿至指定的刻度標記，設定鍵盤的重複率。  
  
 這個控制項 (並因此`CSliderCtrl`類別) 僅適用於執行 Windows 95/98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 滑桿移動以您在建立時指定的遞增量。 例如，如果您指定滑桿，應該有五個範圍，滑桿可只能佔用六個位置︰ 一個位置是在左邊的滑桿控制項和每個遞增量範圍中的一個位置。 一般來說，這些位置的每一個都以刻度標記來識別。  
  
 使用建構函式建立有個滑桿和**建立**成員函式`CSliderCtrl`。 一旦您建立的滑桿控制項，您可以使用成員函式`CSliderCtrl`變更許多屬性。 您可以進行的變更包括設定滑桿的最小和最大位置、繪製刻度標記、設定選取範圍，以及重新調整滑桿定位。  
  
 如需有關使用`CSliderCtrl`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="clearsel"></a>CSliderCtrl::ClearSel  
 清除目前的選取範圍中的滑桿控制項。  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bRedraw`  
 重繪旗標。 如果這個參數是**TRUE**，滑桿會重新繪製之後會清除選取範圍, 否則滑動軸不重新繪製。  
  
##  <a name="cleartics"></a>CSliderCtrl::ClearTics  
 滑桿控制項，會移除目前的刻度標記。  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `bRedraw`  
 重繪旗標。 如果這個參數是**TRUE**，滑桿會重新繪製刻度標記會清除之後; 否則滑動軸不重新繪製。  
  
##  <a name="create"></a>CSliderCtrl::Create  
 建立滑桿控制項，並將它附加`CSliderCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定滑桿控制項的樣式。 套用的任何結合[滑桿控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，來控制。  
  
 `rect`  
 指定滑桿控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 指定滑桿控制項的父視窗，通常`CDialog`。 它不得為**NULL**。  
  
 `nID`  
 指定滑桿控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CSliderCtrl`兩個步驟。 首先，呼叫建構函式，並接著呼叫**建立**，其建立滑桿控制項，並將它附加`CSliderCtrl`物件。  
  
 根據設定值`dwStyle`，滑桿控制項可以具有垂直或水平方向。 它可以有刻度任一邊邊緣，或兩者皆非。 它也可以用來指定連續值的範圍。  
  
 若要將延伸的視窗樣式套用至滑桿控制項，呼叫[CreateEx](#createex)而不是**建立**。  
  
##  <a name="createex"></a>CSliderCtrl::CreateEx  
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
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定滑桿控制項的樣式。 套用的任何結合[滑桿控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，來控制。  
  
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
  
##  <a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl  
 建構 `CSliderCtrl` 物件。  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>CSliderCtrl::GetBuddy  
 擷取在指定位置的滑桿控制項協同視窗的控制代碼。  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 `fLocation`  
 布林值，指出這兩個協同視窗控制代碼，來擷取。 可為下列其中一個值：  
  
- **TRUE**擷取左邊的滑桿朋友的控制代碼。 如果滑桿控制項使用`TBS_VERT`樣式，訊息將會擷取滑桿上方朋友。  
  
- **FALSE**擷取滑桿向朋友的控制代碼。 如果滑桿控制項使用`TBS_VERT`樣式，訊息將會擷取以下滑桿朋友。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)協同視窗，在所指定的位置的物件`fLocation`，或**NULL**如果沒有協同視窗存在於該位置。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getchannelrect"></a>CSliderCtrl::GetChannelRect  
 擷取的大小和位置，這個周框的滑桿控制項的通道。  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>參數  
 `lprc`  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)函式傳回時包含的大小和位置的通道物件的週框。  
  
### <a name="remarks"></a>備註  
 通道是透過將滑桿移和其中包含反白顯示的選取範圍時的區域。  
  
##  <a name="getlinesize"></a>CSliderCtrl::GetLineSize  
 擷取的程式行，滑桿控制項的大小。  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項的程式碼行的大小。  
  
### <a name="remarks"></a>備註  
 線條大小會影響多少滑桿移動的**TB_LINEUP**和**TB_LINEDOWN**通知。 線條大小的預設值為 1。  
  
##  <a name="getnumtics"></a>CSliderCtrl::GetNumTics  
 擷取滑桿控制項中的刻度數。  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項中的刻度數。  
  
##  <a name="getpagesize"></a>CSliderCtrl::GetPageSize  
 擷取滑桿控制項的頁面的大小。  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿控制項之頁面的大小。  
  
### <a name="remarks"></a>備註  
 多少滑桿移動的頁面大小會影響**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="getpos"></a>CSliderCtrl::GetPos  
 擷取滑桿的滑桿控制項中目前的位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前位置。  
  
##  <a name="getrange"></a>CSliderCtrl::GetRange  
 擷取滑桿控制項在滑桿的最大和最小位置。  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>參數  
 `nMin`  
 整數，接收的最小位置參考。  
  
 `nMax`  
 整數，接收的最大位置參考。  
  
### <a name="remarks"></a>備註  
 此函式將值複製到所參考的整數`nMin`和`nMax`。  
  
##  <a name="getrangemax"></a>CSliderCtrl::GetRangeMax  
 擷取滑桿控制項中的最大位置。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項的最大的位置。  
  
##  <a name="getrangemin"></a>CSliderCtrl::GetRangeMin  
 擷取滑桿控制項中的最小位置。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項的最小位置。  
  
##  <a name="getselection"></a>CSliderCtrl::GetSelection  
 擷取滑桿控制項中目前的選取範圍的開始和結束位置。  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>參數  
 `nMin`  
 接收目前的選取範圍的開始位置的整數的參考。  
  
 `nMax`  
 接收目前的選取範圍的結束位置的整數的參考。  
  
##  <a name="getthumblength"></a>CSliderCtrl::GetThumbLength  
 擷取目前 trackbar 控制項中的滑桿的長度。  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>傳回值  
 滑桿，像素為單位的長度。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getthumbrect"></a>CSliderCtrl::GetThumbRect  
 擷取的大小和滑桿 （捲動方塊），這個周框的滑桿控制項中的位置。  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>參數  
 `lprc`  
 指標`CRect`函式傳回時包含滑桿的週框物件。  
  
##  <a name="gettic"></a>CSliderCtrl::GetTic  
 擷取滑桿控制項中的刻度標記位置。  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>參數  
 `nTic`  
 識別以刻度標記以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 指定的刻度標記或-1，否則位置`nTic`未指定有效的索引。  
  
##  <a name="getticarray"></a>CSliderCtrl::GetTicArray  
 擷取陣列，其中包含的刻度標記的滑桿控制項位置的位址。  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列，包含滑桿控制項的刻度標記位置的位址。  
  
##  <a name="getticpos"></a>CSliderCtrl::GetTicPos  
 擷取刻度標記的滑桿控制項中的目前實體的位置。  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>參數  
 `nTic`  
 識別以刻度標記以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 實體位置，用戶端座標中指定的刻度標記或 – 1，否則`nTic`未指定有效的索引。  
  
##  <a name="gettooltips"></a>CSliderCtrl::GetToolTips  
 如果有的話，請擷取指派給控制項的滑桿，工具提示控制項的控制代碼。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件，或**NULL**如果工具提示不在使用中。 如果滑桿控制項不會使用**TBS_TOOLTIPS**樣式，則傳回值是**NULL**。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 請注意，此成員函式傳回`CToolTipCtrl`物件而不是控制項的控制代碼。  
  
 滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setbuddy"></a>CSliderCtrl::SetBuddy  
 將視窗指派為協同視窗的滑桿控制項。  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pWndBuddy`  
 指標`CWnd`會被設定為協同滑桿控制項的物件。  
  
 `fLocation`  
 值，指定用來顯示協同視窗的位置。 這個值可以是下列其中一項︰  
  
- **TRUE**如果 trackbar 控制項使用，將會出現 trackbar 左邊的好友`TBS_HORZ`樣式。 如果使用 trackbar`TBS_VERT`樣式，好友上方 trackbar 控制項。  
  
- **FALSE**如果 trackbar 控制項使用，將會出現 trackbar 右邊的好友`TBS_HORZ`樣式。 如果使用 trackbar`TBS_VERT`樣式，好友下方 trackbar 控制項。  
  
### <a name="return-value"></a>傳回值  
 指標[CWnd](../../mfc/reference/cwnd-class.md)先前指派給該位置的滑桿控制項的物件。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 請注意，此成員函式會使用指標`CWnd`物件，而不是其傳回值和參數的視窗控制代碼。  
  
 滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setlinesize"></a>CSliderCtrl::SetLineSize  
 設定滑桿控制項之線條的大小。  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 `nSize`  
 滑桿控制項的新線條大小。  
  
### <a name="return-value"></a>傳回值  
 先前的線條大小。  
  
### <a name="remarks"></a>備註  
 線條大小會影響多少滑桿移動的**TB_LINEUP**和**TB_LINEDOWN**通知。  
  
##  <a name="setpagesize"></a>CSliderCtrl::SetPageSize  
 設定滑桿控制項的頁面大小。  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>參數  
 `nSize`  
 滑桿控制項的新的頁面大小。  
  
### <a name="return-value"></a>傳回值  
 先前的頁面大小。  
  
### <a name="remarks"></a>備註  
 多少滑桿移動的頁面大小會影響**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="setpos"></a>CSliderCtrl::SetPos  
 將滑桿的目前位置設定滑桿控制項。  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>參數  
 `nPos`  
 指定新的滑桿位置。  
  
##  <a name="setrange"></a>CSliderCtrl::SetRange  
 滑桿控制項中的設定範圍 （最小和最大位置）。  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `nMin`  
 滑桿的最小位置。  
  
 `nMax`  
 最大滑桿的位置。  
  
 `bRedraw`  
 重繪的旗標。 如果這個參數是**TRUE**，滑桿範圍會設定之後會重新繪製; 否則滑動軸不重新繪製。  
  
##  <a name="setrangemax"></a>CSliderCtrl::SetRangeMax  
 滑桿控制項中的設定最大範圍。  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `nMax`  
 最大滑桿的位置。  
  
 `bRedraw`  
 重繪的旗標。 如果這個參數是**TRUE**，滑桿範圍會設定之後會重新繪製; 否則滑動軸不重新繪製。  
  
##  <a name="setrangemin"></a>CSliderCtrl::SetRangeMin  
 滑桿控制項中的設定最小範圍。  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>參數  
 `nMin`  
 滑桿的最小位置。  
  
 `bRedraw`  
 重繪的旗標。 如果這個參數是**TRUE**，滑桿範圍會設定之後會重新繪製; 否則滑動軸不重新繪製。  
  
##  <a name="setselection"></a>CSliderCtrl::SetSelection  
 設定目前的選取範圍的開始和結束位置中的滑桿控制項。  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>參數  
 `nMin`  
 滑桿的開始位置。  
  
 `nMax`  
 結束滑桿的位置。  
  
##  <a name="setthumblength"></a>CSliderCtrl::SetThumbLength  
 設定目前 trackbar 控制項中的滑桿的長度。  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `nLength`|滑桿，像素為單位的長度。|  
  
### <a name="remarks"></a>備註  
 此方法需要 trackbar 控制項設定為[TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147)樣式。  
  
 這個方法會傳送[TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_sliderCtrl`，也就是用來存取目前 trackbar 控制項。 此範例也會定義變數， `thumbLength`，也就是用來儲存 trackbar 控制項的捲動方塊元件的預設長度。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定 trackbar 控制項的捲動方塊元件兩次，其預設長度。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>CSliderCtrl::SetTic  
 滑桿控制項中設定刻度的位置。  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>參數  
 `nTic`  
 刻度的位置。 這個參數必須指定為正整數值。  
  
### <a name="return-value"></a>傳回值  
 設定刻度標記; 如果為非零否則為 0。  
  
##  <a name="setticfreq"></a>CSliderCtrl::SetTicFreq  
 設定與哪一個刻度標記會顯示在有個滑桿的頻率。  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>參數  
 *nFreq*  
 刻度的頻率。  
  
### <a name="remarks"></a>備註  
 例如，如果頻率設定為 2 時，刻度標記會顯示個滑桿的範圍內的遞增量。 預設設定的頻率 1 （也就是每次累加範圍中的是以刻度標記與相關聯）。  
  
 您必須建立與控制項`TBS_AUTOTICKS`使用此函數的樣式。 如需詳細資訊，請參閱[CSliderCtrl::Create](#create)。  
  
##  <a name="settipside"></a>CSliderCtrl::SetTipSide  
 Trackbar 控制項位置的工具提示控制項使用。  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>參數  
 `nLocation`  
 值，表示要顯示工具提示控制項的位置。 如需可能值的清單，請參閱的 Win32 訊息[TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 值，表示工具提示控制項的上一個位置。 傳回的值等於其中一個可能的值為`nLocation`。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為**TBM_SETTIPSIDE**所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 滑桿控制項，使用**TBS_TOOLTIPS**樣式顯示工具提示。 滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
##  <a name="settooltips"></a>CSliderCtrl::SetToolTips  
 將工具提示控制項指派給滑桿控制項。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>參數  
 `pWndTip`  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件，其中包含要使用滑桿控制項的工具提示。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 使用滑桿控制項建立時**TBS_TOOLTIPS**樣式，它會建立預設的工具提示控制項的滑桿旁，顯示目前的滑桿的位置出現。 滑桿控制項樣式的說明，請參閱[Trackbar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl 類別](../../mfc/reference/cprogressctrl-class.md)

