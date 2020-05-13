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
ms.openlocfilehash: c9e94e334318b32efcf8c9de681a78349ab12151
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751132"
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
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|建構 `CProgressCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CProgressCtrl::建立](#create)|創建進度條控制項並將其附加到`CProgressCtrl`物件。|
|[CProgressCtrl::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建進度控制項,並將`CProgressCtrl`其附加到 物件。|
|[CProgressCtrl::獲取巴彩](#getbarcolor)|獲取當前進度條控件的進度指示器列的顏色。|
|[CProgressCtrl::GetBkColor](#getbkcolor)|獲取當前進度列的背景顏色。|
|[CProgressCtrl::取得Pos](#getpos)|獲取進度條的當前位置。|
|[CProgressCtrl:取得範圍](#getrange)|獲取進度條控制範圍的下限和上限。|
|[CProgressCtrl::取得狀態](#getstate)|獲取當前進度條控件的狀態。|
|[CProgressCtrl:抓取步驟](#getstep)|檢索當前進度條控件的進度條的步長增量。|
|[CProgressCtrl::偏移波](#offsetpos)|按指定增量推進進度條控制項的當前位置,然後重繪條形以反映新位置。|
|[CProgressCtrl::設定欄顏色](#setbarcolor)|設置當前進度條控制器中的進度指示器列的顏色。|
|[CProgressCtrl::SetBkColor](#setbkcolor)|設置進度列的背景顏色。|
|[CProgressCtrl::SetMarquee](#setmarquee)|為當前進度條控件打開或關閉選框模式。|
|[CProgressCtrl::SetPos](#setpos)|設置進度條控制的當前位置,並重繪條形以反映新位置。|
|[CProgressCtrl::設定範圍](#setrange)|設置進度條控制的最小和最大範圍,並重繪條形以反映新範圍。|
|[CProgressCtrl::設定狀態](#setstate)|設定目前進度列控制項的狀態。|
|[CProgressCtrl::設定步驟](#setstep)|指定進度條控制的步長增量。|
|[CProgressCtrl::步驟](#stepit)|按步長增量推進進度條控制項的目前位置(請參閱[SetStep),](#setstep)然後重繪條形以反映新位置。|

## <a name="remarks"></a>備註

進度條控制項是應用程式可用於指示長時間操作進度的視窗。 它由從左至右逐漸填充的矩形組成,系統在操作過程中突出顯示顏色。

進度條控制項具有範圍和當前位置。 範圍表示操作的總持續時間,當前位置表示應用程式在完成操作時所做的進度。 視窗過程使用範圍和當前位置來確定進度條的百分比以填充高光顏色。 由於範圍和當前位置值以已簽名整數表示,因此當前倉位值的可能範圍為 -2,147,483,648 到 2,147,483,647(含)。

有關`CProgressCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[與使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl::CProgressCtrl

建構 `CProgressCtrl` 物件。

```
CProgressCtrl();
```

### <a name="remarks"></a>備註

建構`CProgressCtrl`物件後,調`CProgressCtrl::Create`用 以創建進度條控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl::建立

創建進度條控制項並將其附加到`CProgressCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定進度條控制項的樣式。 除了以下進度列控制元件樣式外,將 Windows SDK 中的[「建立視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)」中描述的視窗樣式的任意組合應用於控制項:

- PBS_VERTICAL垂直顯示進度資訊,從上到下。 如果沒有此標誌,進度條控制項將水準(從左至右)顯示。

- PBS_SMOOTH 在進度條控件中顯示逐漸、平滑的填充。 如果沒有此標誌,控件將填充塊。

*矩形*<br/>
指定進度條控制的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。 由於控件必須是子視窗,因此指定的座標相對於*pParentWnd*的工作區。

*pparentwnd*<br/>
指定進度列件的父視窗,通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定進度條控制項的識別碼。

### <a name="return-value"></a>傳回值

如果物件已成功`CProgressCtrl`創建,則為 TRUE;如果物件已成功創建,則為 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

分兩步`CProgressCtrl`構造物件。 首先調用構造函數,該構造函數創建`CProgressCtrl`對象,然後`Create`調用 ,這將創建進度條控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl::創建Ex

創建控制項(子視窗),並將其與`CProgressCtrl`物件關聯。

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
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定進度條控制項的樣式。 應用 Windows SDK 中[建立視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)中描述的視窗樣式的任意組合。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl::獲取巴彩

獲取當前進度條控件的進度指示器列的顏色。

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>傳回值

目前進度條的顏色(表示為[COLORREF](/windows/win32/gdi/colorref)值)或CLR_DEFAULT如果進度指示器條顏色為預設顏色。

### <a name="remarks"></a>備註

此方法發送[PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor)消息,這在 Windows SDK 中介紹。

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl::GetBkColor

獲取當前進度列的背景顏色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

目前進度條的背景顏色,表示為[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

此方法發送[PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor)消息,這在 Windows SDK 中介紹。

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl::取得Pos

檢索進度條的當前位置。

```
int GetPos();
```

### <a name="return-value"></a>傳回值

進度條控制項的位置。

### <a name="remarks"></a>備註

進度條控制項的位置不是螢幕上的物理位置,而是在[SetRange](#setrange)中指示的上下範圍之間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl:取得範圍

獲取進度條控制項的當前下限和上限或範圍。

```cpp
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>參數

*n 更低*<br/>
對接收進度條控件下限的整數的引用。

*n*<br/>
對接收進度條控件上限的整數的引用。

### <a name="remarks"></a>備註

此函數分別將下限和上限的值複製到*nLower*和*nUpper*引用的整數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl::取得狀態

獲取當前進度條控件的狀態。

```
int GetState() const;
```

### <a name="return-value"></a>傳回值

當前進度條控制項的狀態,這是以下值之一:

|值|State|
|-----------|-----------|
|PBST_NORMAL|進行中|
|PBST_ERROR|錯誤|
|PBST_PAUSED|已暫停|

### <a name="remarks"></a>備註

此方法發送[PBM_GETSTATE](/windows/win32/Controls/pbm-getstate)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

以下代碼示例檢索當前進度條控制者的狀態。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl:抓取步驟

檢索當前進度條控件的進度條的步長增量。

```
int GetStep() const;
```

### <a name="return-value"></a>傳回值

進度條的步驟增量。

### <a name="remarks"></a>備註

步驟增量是調用[CProgressCtrl::Step 它](#stepit)增加進度條的當前位置的量。

此方法發送[PBM_GETSTEP](/windows/win32/Controls/pbm-getstep)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

以下代碼示例檢索當前進度條控制件的步長增量。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl::偏移波

通過*nPos*指定的增量推進進度條控制項的當前位置,然後重繪條形以反映新位置。

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
預付頭寸的金額。

### <a name="return-value"></a>傳回值

進度條控件的上一個位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl::設定欄顏色

設置當前進度條控制器中的進度指示器列的顏色。

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*clrBar*|[在]指定進度指示器列的新顏色的[COLORREF](/windows/win32/gdi/colorref)值。 指定CLR_DEFAULT使進度條使用其預設顏色。|

### <a name="return-value"></a>傳回值

進度指示器列的前一顏色(表示為[COLORREF](/windows/win32/gdi/colorref)值)或CLR_DEFAULT如果進度指示器列的顏色為預設顏色。

### <a name="remarks"></a>備註

僅當 Windows Vista 主題無效時,該方法才會設置進度[theme](/windows/win32/Controls/visual-styles-overview)`SetBarColor`條顏色。

此方法發送[PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

以下代碼示例將進度條的顏色更改為紅色、綠色、藍色或預設值。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl::SetBkColor

設置進度列的背景顏色。

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>參數

*clrNew*<br/>
指定新背景顏色的 COLORREF 值。 指定CLR_DEFAULT值以使用進度條的預設背景顏色。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值指示以前的背景顏色,如果背景顏色為預設顏色,則CLR_DEFAULT。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl::SetMarquee

為當前進度條控件打開或關閉選框模式。

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*fMarqueeMode*|[在]TRUE 可打開選框模式,或 FALSE 關閉選框模式。|
|*N 間隔*|[在]選取框動畫更新之間的時間(以毫秒為單位)。|

### <a name="return-value"></a>傳回值

此方法始終返回 TRUE。

### <a name="remarks"></a>備註

啟用選取框模式后,進度列將設置動畫,並像影院選框上的符號一樣滾動。

此方法發送[PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

以下代碼示例啟動並停止選取框滾動動畫。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl::SetPos

設置*nPos*指定的進度條控制的目前位置,並重繪條形以反映新位置。

```
int SetPos(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
進度條控制項的新位置。

### <a name="return-value"></a>傳回值

進度條控件的上一個位置。

### <a name="remarks"></a>備註

進度條控制項的位置不是螢幕上的物理位置,而是在[SetRange](#setrange)中指示的上下範圍之間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl::設定範圍

設置進度條控制項範圍的上限和下限,並重繪條形以反映新範圍。

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>參數

*n 更低*<br/>
指定範圍的下限(預設值為零)。

*n*<br/>
指定範圍的上限(預設值為100)。

### <a name="remarks"></a>備註

成員函數`SetRange32`為進度控制設置 32 位範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl::設定狀態

設定目前進度列控制項的狀態。

```
int SetState(int iState);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*i國家*|[在]要設置進度條的狀態。 請使用下列其中一個值：<br /><br /> - PBST_NORMAL - 正在進行中<br />- PBST_ERROR - 錯誤<br />- PBST_PAUSED - 暫停|

### <a name="return-value"></a>傳回值

目前進度列控制項先前的狀態。

### <a name="remarks"></a>備註

此方法發送[PBM_SETSTATE](/windows/win32/Controls/pbm-setstate)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下列程式碼範例會定義變數 `m_progressCtrl`，用來以程式設計方式存取進度列控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>範例

下列程式碼範例會將目前進度列控制項的狀態設定為已暫停或進行中。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl::設定步驟

指定進度條控制的步長增量。

```
int SetStep(int nStep);
```

### <a name="parameters"></a>參數

*n步步*<br/>
新步驟增量。

### <a name="return-value"></a>傳回值

上一步增量。

### <a name="remarks"></a>備註

步驟增量是調用`CProgressCtrl::StepIt`增加進度條的當前位置的金額。

默認步驟增量為 10。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl::步驟

按步長增量推進進度條控件的當前位置,然後重繪條以反映新位置。

```
int StepIt();
```

### <a name="return-value"></a>傳回值

進度條控件的上一個位置。

### <a name="remarks"></a>備註

步驟增量由`CProgressCtrl::SetStep`成員函數設置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
