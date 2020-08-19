---
title: CProgressCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: eda19ca2b94978201806e60d2ae8399e00e13f1f
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561514"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl 類別

提供 Windows 通用進度列控制項的功能。

## <a name="syntax"></a>語法

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CProgressCtrl：： CProgressCtrl](#cprogressctrl)|建構 `CProgressCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CProgressCtrl：： Create](#create)|建立進度列控制項並將其附加至 `CProgressCtrl` 物件。|
|[CProgressCtrl：： CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的進度控制項，並將其附加至 `CProgressCtrl` 物件。|
|[CProgressCtrl：： GetBarColor](#getbarcolor)|取得目前進度列控制項的進度指標列色彩。|
|[CProgressCtrl：： GetBkColor](#getbkcolor)|取得目前進度列的背景色彩。|
|[CProgressCtrl：： GetPos](#getpos)|取得進度列的目前位置。|
|[CProgressCtrl：： GetRange](#getrange)|取得進度列控制項範圍的下限和上限。|
|[CProgressCtrl：： >getstate](#getstate)|取得目前進度列控制項的狀態。|
|[CProgressCtrl：： GetStep](#getstep)|抓取目前進度列控制項進度列的步驟增量。|
|[CProgressCtrl：： OffsetPos](#offsetpos)|依指定的遞增量將進度列控制項的目前位置往前移，並重新繪製橫條以反映新的位置。|
|[CProgressCtrl：： SetBarColor](#setbarcolor)|在目前的進度列控制項中設定進度指標列的色彩。|
|[CProgressCtrl：： SetBkColor](#setbkcolor)|設定進度列的背景色彩。|
|[CProgressCtrl：： SetMarquee](#setmarquee)|開啟或關閉目前進度列控制項的捲軸模式。|
|[CProgressCtrl：： SetPos](#setpos)|設定進度列控制項的目前位置，並重新繪製橫條以反映新的位置。|
|[CProgressCtrl：： SetRange](#setrange)|設定進度列控制項的最小和最大範圍，並重新繪製橫條以反映新的範圍。|
|[CProgressCtrl：： SetState](#setstate)|設定目前進度列控制項的狀態。|
|[CProgressCtrl：： SetStep](#setstep)|指定進度列控制項的步驟增量。|
|[CProgressCtrl：： StepIt](#stepit)|將進度列控制項的目前位置往前移 (查看 [SetStep](#setstep)) ，然後重新繪製橫條以反映新的位置。|

## <a name="remarks"></a>備註

進度列控制項是一種視窗，可讓應用程式用來指出冗長作業的進度。 它是由從左至右逐漸填滿的矩形所組成，而且系統會在作業進行時醒目提示色彩。

進度列控制項具有範圍和目前的位置。 範圍代表作業的總持續時間，而目前的位置則代表應用程式完成作業所進行的進度。 視窗程式會使用範圍和目前的位置，來決定要以醒目提示色彩填滿的進度列百分比。 因為範圍和目前的位置值以帶正負號的整數表示，所以目前位置值的可能範圍是從-2147483648 到2147483647（含）。

如需使用的詳細資訊 `CProgressCtrl` ，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a> CProgressCtrl：： CProgressCtrl

建構 `CProgressCtrl` 物件。

```
CProgressCtrl();
```

### <a name="remarks"></a>備註

在建立 `CProgressCtrl` 物件之後，呼叫 `CProgressCtrl::Create` 以建立進度列控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a> CProgressCtrl：： Create

建立進度列控制項並將其附加至 `CProgressCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定進度列控制項的樣式。 將 [Windows SDK 中的](/windows/win32/api/winuser/nf-winuser-createwindoww) [視窗 stylesdescribed] 的任何組合（除了下列進度列控制項樣式以外）套用至控制項：

- PBS_VERTICAL 垂直顯示進度資訊（從上到下）。 如果沒有這個旗標，進度列控制項會以水準方式（由左至右）顯示。

- PBS_SMOOTH 會顯示進度列控制項的逐漸、平滑地填滿。 如果沒有這個旗標，控制項就會填滿區塊。

*矩形*<br/>
指定進度列控制項的大小和位置。 它可以是 [CRect](../../atl-mfc-shared/reference/crect-class.md) 物件或 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構。 因為控制項必須是子視窗，所以指定的座標是相對於 *pParentWnd*的工作區。

*pParentWnd*<br/>
指定進度列控制項的父視窗，通常是 `CDialog` 。 它不得為 NULL。

*nID*<br/>
指定進度列控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功建立物件則為 TRUE， `CProgressCtrl` 否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用 `CProgressCtrl` 兩個步驟來建立物件。 首先，呼叫可建立物件的函式， `CProgressCtrl` 然後呼叫 `Create` ，以建立進度列控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a> CProgressCtrl：： CreateEx

 (子視窗) 建立控制項，並將它與物件產生關聯 `CProgressCtrl` 。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定進度列控制項的樣式。 套用 Windows SDK 中的 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 所述的任何視窗樣式組合。

*矩形*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，描述要建立之視窗的大小和位置（以*pParentWnd*的用戶端座標表示）。

*pParentWnd*<br/>
視窗的指標，該視窗為控制項的父代。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用 `CreateEx` instead Of [Create](#create) 來套用延伸的 windows 樣式（依 Windows 擴充樣式的 "前言 **WS_EX_** 指定）。

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a> CProgressCtrl：： GetBarColor

取得目前進度列控制項的進度指標列色彩。

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>傳回值

目前進度列的色彩（以 [COLORREF](/windows/win32/gdi/colorref) 值表示）或 CLR_DEFAULT （如果進度指示器列色彩是預設色彩）。

### <a name="remarks"></a>備註

這個方法會傳送 [PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor) 的訊息，如 Windows SDK 中所述。

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a> CProgressCtrl：： GetBkColor

取得目前進度列的背景色彩。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

目前進度列的背景色彩，以 [COLORREF](/windows/win32/gdi/colorref) 值表示。

### <a name="remarks"></a>備註

這個方法會傳送 [PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor) 的訊息，如 Windows SDK 中所述。

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a> CProgressCtrl：： GetPos

抓取進度列的目前位置。

```
int GetPos();
```

### <a name="return-value"></a>傳回值

進度列控制項的位置。

### <a name="remarks"></a>備註

進度列控制項的位置不是螢幕上的實體位置，而是在 [SetRange](#setrange)中指出的上方和下限範圍之間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a> CProgressCtrl：： GetRange

取得進度列控制項目前的下限和上限，或範圍。

```cpp
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>參數

*nLower*<br/>
整數的參考，可接收進度列控制項的下限值。

*nUpper*<br/>
整數的參考，可接收進度列控制項的上限。

### <a name="remarks"></a>備註

此函式會將下限和上限的值分別複製到 *nLower* 和 *nUpper*所參考的整數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a> CProgressCtrl：： >getstate

取得目前進度列控制項的狀態。

```
int GetState() const;
```

### <a name="return-value"></a>傳回值

目前進度列控制項的狀態，這是下列其中一個值：

|值|State|
|-----------|-----------|
|PBST_NORMAL|正在進行|
|PBST_ERROR|錯誤|
|PBST_PAUSED|已暫停|

### <a name="remarks"></a>備註

這個方法會傳送 [PBM_GETSTATE](/windows/win32/Controls/pbm-getstate) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

下列程式碼範例會抓取目前進度列控制項的狀態。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a> CProgressCtrl：： GetStep

抓取目前進度列控制項進度列的步驟增量。

```
int GetStep() const;
```

### <a name="return-value"></a>傳回值

進度列的步驟增量。

### <a name="remarks"></a>備註

步驟遞增是 [CProgressCtrl：： StepIt](#stepit) 的呼叫增加進度列目前位置的數量。

這個方法會傳送 [PBM_GETSTEP](/windows/win32/Controls/pbm-getstep) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

下列程式碼範例會抓取目前進度列控制項的步驟增量。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a> CProgressCtrl：： OffsetPos

依 *nPos* 所指定的遞增量將進度列控制項的目前位置往前移，並重新繪製橫條以反映新的位置。

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要預先放置位置的數量。

### <a name="return-value"></a>傳回值

進度列控制項的先前位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a> CProgressCtrl：： SetBarColor

在目前的進度列控制項中設定進度指標列的色彩。

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>參數

*clrBar*\
在 [COLORREF](/windows/win32/gdi/colorref) 值，指定進度指標列的新色彩。 指定 CLR_DEFAULT，使進度列使用其預設色彩。

### <a name="return-value"></a>傳回值

進度指標列的上一個色彩（以 [COLORREF](/windows/win32/gdi/colorref) 值表示），如果進度指標列的色彩是預設色彩，則為 CLR_DEFAULT。

### <a name="remarks"></a>備註

`SetBarColor`只有在 Windows Vista[主題](/windows/win32/Controls/visual-styles-overview)未生效時，此方法才會設定進度列色彩。

這個方法會傳送 [PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

下列程式碼範例會將進度列的色彩變更為紅色、綠色、藍色或預設值。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a> CProgressCtrl：： SetBkColor

設定進度列的背景色彩。

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>參數

*clrNew*<br/>
COLORRE光圈值，指定新的背景色彩。 指定 CLR_DEFAULT 值，以使用進度列的預設背景色彩。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值，指出先前的背景色彩，或 CLR_DEFAULT 背景色彩是否為預設色彩。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a> CProgressCtrl：： SetMarquee

開啟或關閉目前進度列控制項的捲軸模式。

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>參數

*fMarqueeMode*\
在TRUE 表示開啟 [字幕] 模式，或 [FALSE] 表示關閉 [字幕] 模式。

*N 間隔*\
在滾動字幕動畫更新之間的時間（以毫秒為單位）。

### <a name="return-value"></a>傳回值

這個方法一律會傳回 TRUE。

### <a name="remarks"></a>備註

當 [字幕] 模式開啟時，進度列會以動畫顯示，並像劇院字幕一樣地滾動。

這個方法會傳送 [PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

下列程式碼範例會啟動和停止字幕滾動動畫。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a> CProgressCtrl：： SetPos

依 *nPos* 的指定設定進度列控制項的目前位置，並重新繪製橫條以反映新的位置。

```
int SetPos(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
進度列控制項的新位置。

### <a name="return-value"></a>傳回值

進度列控制項的先前位置。

### <a name="remarks"></a>備註

進度列控制項的位置不是螢幕上的實體位置，而是在 [SetRange](#setrange)中指出的上方和下限範圍之間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a> CProgressCtrl：： SetRange

設定進度列控制項範圍的上限和下限，並重新繪製橫條以反映新的範圍。

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>參數

*nLower*<br/>
指定範圍 (預設值為零) 的下限。

*nUpper*<br/>
指定範圍 (預設值為 100) 的上限。

### <a name="remarks"></a>備註

成員函 `SetRange32` 式會設定進度控制項的32位範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a> CProgressCtrl：： SetState

設定目前進度列控制項的狀態。

```
int SetState(int iState);
```

### <a name="parameters"></a>參數

*iState*\
在要設定進度列的狀態。 請使用下列其中一個值：

- `PBST_NORMAL` -進行中
- `PBST_ERROR` -錯誤
- `PBST_PAUSED` - 已暫停

### <a name="return-value"></a>傳回值

目前進度列控制項先前的狀態。

### <a name="remarks"></a>備註

這個方法會傳送 [PBM_SETSTATE](/windows/win32/Controls/pbm-setstate) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

下列程式碼範例會將目前進度列控制項的狀態設定為已暫停或進行中。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a> CProgressCtrl：： SetStep

指定進度列控制項的步驟增量。

```
int SetStep(int nStep);
```

### <a name="parameters"></a>參數

*nStep*<br/>
新步驟增量。

### <a name="return-value"></a>傳回值

上一個步驟遞增。

### <a name="remarks"></a>備註

步驟遞增是用來 `CProgressCtrl::StepIt` 增加進度列目前位置的呼叫數量。

預設步驟增量為10。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a> CProgressCtrl：： StepIt

將進度列控制項的目前位置往前移，並重新繪製橫條以反映新的位置。

```
int StepIt();
```

### <a name="return-value"></a>傳回值

進度列控制項的先前位置。

### <a name="remarks"></a>備註

步驟遞增是由成員函式所設定 `CProgressCtrl::SetStep` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
