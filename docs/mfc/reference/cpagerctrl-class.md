---
title: CPagerCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: 9b3af31e7d352e93144cde0c321620693111e145
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561904"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl 類別

`CPagerCtrl` 類別會封裝 Windows 頁面巡覽區控制項，可以將不符合容器視窗大小的包含視窗捲動到檢視中。

## <a name="syntax"></a>語法

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPagerCtrl：： CPagerCtrl](#cpagerctrl)|建構 `CPagerCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPagerCtrl：： Create](#create)|使用指定的樣式建立分頁控制項，並將它附加至目前的 `CPagerCtrl` 物件。|
|[CPagerCtrl：： CreateEx](#createex)|使用指定的擴充樣式建立分頁控制項，並將它附加至目前的 `CPagerCtrl` 物件。|
|[CPagerCtrl：： ForwardMouse](#forwardmouse)|啟用或停用將 [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) 訊息轉送至目前的呼機控制項中所包含的視窗。|
|[CPagerCtrl：： GetBkColor](#getbkcolor)|抓取目前呼機控制項的背景色彩。|
|[CPagerCtrl：： GetBorder](#getborder)|抓取目前呼機控制項的框線大小。|
|[CPagerCtrl：： GetButtonSize](#getbuttonsize)|抓取目前呼機控制項的按鈕大小。|
|[CPagerCtrl：： GetButtonState](#getbuttonstate)|抓取目前呼機控制項中指定之按鈕的狀態。|
|[CPagerCtrl：： GetDropTarget](#getdroptarget)|抓取目前呼機控制項的 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 介面。|
|[CPagerCtrl：： GetScrollPos](#getscrollpos)|抓取目前呼機控制項的滾動位置。|
|[CPagerCtrl：： IsButtonDepressed](#isbuttondepressed)|指出目前呼機控制項的指定按鈕是否處於 `pressed` 狀態。|
|[CPagerCtrl：： IsButtonGrayed](#isbuttongrayed)|指出目前呼機控制項的指定按鈕是否處於 `grayed` 狀態。|
|[CPagerCtrl：： IsButtonHot](#isbuttonhot)|指出目前呼機控制項的指定按鈕是否處於 `hot` 狀態。|
|[CPagerCtrl：： IsButtonInvisible](#isbuttoninvisible)|指出目前呼機控制項的指定按鈕是否處於 `invisible` 狀態。|
|[CPagerCtrl：： IsButtonNormal](#isbuttonnormal)|指出目前呼機控制項的指定按鈕是否處於 `normal` 狀態。|
|[CPagerCtrl：： RecalcSize](#recalcsize)|導致目前的頁面控制項重新計算包含視窗的大小。|
|[CPagerCtrl：： SetBkColor](#setbkcolor)|設定目前呼機控制項的背景色彩。|
|[CPagerCtrl：： SetBorder](#setborder)|設定目前呼機控制項的框線大小。|
|[CPagerCtrl：： SetButtonSize](#setbuttonsize)|設定目前呼機控制項的按鈕大小。|
|[CPagerCtrl：： SetChild](#setchild)|為目前的頁面控制項設定包含的視窗。|
|[CPagerCtrl：： SetScrollPos](#setscrollpos)|設定目前呼機控制項的滾動位置。|

## <a name="remarks"></a>備註

分頁控制項是一個視窗，其中包含線性和大於包含視窗的另一個視窗，可讓您將包含的視窗滾動到視野中。 當包含的視窗滾動至最遠的範圍時，分頁控制項會顯示兩個自動消失的滾動按鈕，否則會自動消失。 您可以建立以水準或垂直方式滾動的呼機控制項。

例如，如果您的應用程式所擁有的工具列不夠寬，無法顯示其所有專案，您可以將工具列指派給頁面控制項，而且使用者將可以將工具列向左或向右滾動，以存取所有專案。 Microsoft Internet Explorer 4.0 版 ( # A0 4.71 版) 引進了呼機控制項。

`CPagerCtrl`類別衍生自[CWnd](../../mfc/reference/cwnd-class.md)類別。 如需詳細資訊和呼機控制項的圖例，請參閱 [呼機控制項](/windows/win32/Controls/pager-controls)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a> CPagerCtrl：： CPagerCtrl

建構 `CPagerCtrl` 物件。

```
CPagerCtrl();
```

### <a name="remarks"></a>備註

使用 [CPagerCtrl：： create](#create) 或 [CPagerCtrl：： CreateEx](#createex) 方法來建立呼機控制項，並將其附加至 `CPagerCtrl` 物件。

## <a name="cpagerctrlcreate"></a><a name="create"></a> CPagerCtrl：： Create

使用指定的樣式建立分頁控制項，並將它附加至目前的 `CPagerCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*\
在要套用至控制項之 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles) 和 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles) 的位元組合 (或) 。

*矩形*\
在 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構的參考，其中包含控制項在用戶端座標中的位置和大小。

*pParentWnd*\
在 [CWnd](../../mfc/reference/cwnd-class.md) 物件的指標，該物件為控制項的父視窗。 此參數不可以是 NULL。

*nID*\
在控制項的識別碼。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

若要建立呼機控制項，請宣告 `CPagerCtrl` 變數，然後呼叫該變數上的 [CPagerCtrl：： Create](#create) 或 [CPagerCtrl：： CreateEx](#createex) 方法。

### <a name="example"></a>範例

下列範例會建立一個分頁控制項，然後使用 [CPagerCtrl：： SetChild](#setchild) 方法，將非常長的按鈕控制項與頁面控制項產生關聯。 然後，此範例會使用 [CPagerCtrl：： SetButtonSize](#setbuttonsize) 方法，將呼機控制項的高度設定為20圖元，並使用 [CPagerCtrl：： SetBorder](#setborder) 方法將框線粗細設定為1圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a> CPagerCtrl：： CreateEx

使用指定的擴充樣式建立分頁控制項，並將它附加至目前的 `CPagerCtrl` 物件。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*\
在要套用至控制項的擴充樣式的位元組合。 如需詳細資訊，請參閱[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函數的*dwExStyle*參數。

*dwStyle*\
在要套用至控制項之 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles) 和 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles) 的位元組合 (或) 。

*矩形*\
在 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構的參考，其中包含控制項在用戶端座標中的位置和大小。

*pParentWnd*\
在 [CWnd](../../mfc/reference/cwnd-class.md) 物件的指標，該物件為控制項的父視窗。 此參數不可以是 NULL。

*nID*\
在控制項的識別碼。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

若要建立呼機控制項，請宣告 `CPagerCtrl` 變數，然後呼叫該變數上的 [CPagerCtrl：： Create](#create) 或 [CPagerCtrl：： CreateEx](#createex) 方法。

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a> CPagerCtrl：： ForwardMouse

啟用或停用將 [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) 訊息轉送至目前的呼機控制項中所包含的視窗。

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>參數

*bForward*\
在TRUE 表示轉寄滑鼠訊息，或 FALSE 表示不轉寄滑鼠訊息。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) 的訊息，如 Windows SDK 中所述。

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a> CPagerCtrl：： GetBorder

抓取目前呼機控制項的框線大小。

```
int GetBorder() const;
```

### <a name="return-value"></a>傳回值

目前的框線大小（以圖元為單位）。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用 [CPagerCtrl：： GetBorder](#getborder) 方法來取得呼機控制項框線的粗細。

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a> CPagerCtrl：： GetBkColor

抓取目前呼機控制項的背景色彩。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值，其中包含頁面導航控制項目前的背景色彩。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用 [CPagerCtrl：： SetBkColor](#setbkcolor) 方法，將呼機控制項的背景色彩設定為紅色，並使用 [CPagerCtrl：： GetBkColor](#getbkcolor) 方法來確認是否已進行變更。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a> CPagerCtrl：： GetButtonSize

抓取目前呼機控制項的按鈕大小。

```
int GetButtonSize() const;
```

### <a name="return-value"></a>傳回值

目前的按鈕大小（以圖元為單位）。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) 的訊息，如 Windows SDK 中所述。

如果呼機控制項有 PGS_HORZ 樣式，則按鈕大小會決定頁面的寬度，而如果呼機控制項具有 PGS_VERT 樣式，則按鈕大小會決定頁面的高度。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a> CPagerCtrl：： GetButtonState

抓取目前呼機控制項中指定之滾動按鈕的狀態。

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>參數

*iButton*\
在表示要取得狀態的按鈕。 如果有 PGS_HORZ 的呼機控制項樣式，請指定左按鈕的 PGB_TOPORLEFT，然後 PGB_BOTTOMORRIGHT 右鍵按鈕。 如果有 PGS_VERT 的呼機控制項樣式，請針對上方按鈕指定 PGB_TOPORLEFT，然後針對底部按鈕指定 PGB_BOTTOMORRIGHT。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="return-value"></a>傳回值

*IButton*參數所指定之按鈕的狀態。 狀態可以是 PGF_INVISIBLE、PGF_NORMAL、PGF_GRAYED、PGF_DEPRESSED 或 PGF_HOT。 如需詳細資訊，請參閱 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 訊息的傳回值一節。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 的訊息，如 Windows SDK 中所述。

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a> CPagerCtrl：： GetDropTarget

抓取目前呼機控制項的 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 介面。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>傳回值

`IDropTarget`目前呼機控制項介面的指標。

### <a name="remarks"></a>備註

`IDropTarget` 是您在應用程式中支援拖放作業所執行的其中一個介面。

這個方法會傳送 [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) 的訊息，如 Windows SDK 中所述。 當不再需要介面時，此方法的呼叫端會負責呼叫 `Release` [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) 介面的成員。

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a> CPagerCtrl：： GetScrollPos

抓取目前呼機控制項的滾動位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>傳回值

目前的滾動位置，以圖元為單位。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用 [CPagerCtrl：： GetScrollPos](#getscrollpos) 方法來抓取呼機控制項目前的滾動位置。 如果呼機控制項尚未滾動至零，則此範例會使用 [CPagerCtrl：： SetScrollPos](#setscrollpos) 方法將捲軸位置設定為零。

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a> CPagerCtrl：： IsButtonDepressed

指出目前分頁控制項的指定滾動按鈕是否處於按下狀態。

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>參數

*iButton*\
在表示要取得狀態的按鈕。 如果有 PGS_HORZ 的呼機控制項樣式，請指定左按鈕的 PGB_TOPORLEFT，然後 PGB_BOTTOMORRIGHT 右鍵按鈕。 如果有 PGS_VERT 的呼機控制項樣式，請針對上方按鈕指定 PGB_TOPORLEFT，然後針對底部按鈕指定 PGB_BOTTOMORRIGHT。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="return-value"></a>傳回值

如果指定的按鈕處於按下的狀態，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 的訊息，如 Windows SDK 中所述。 然後，它會測試傳回的狀態是否為 PGF_DEPRESSED。 如需詳細資訊，請參閱 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 訊息的傳回值一節。

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a> CPagerCtrl：： IsButtonGrayed

指出目前呼機控制項的指定滾動按鈕是否處於灰色的狀態。

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>參數

*iButton*\
在表示要取得狀態的按鈕。 如果有 PGS_HORZ 的呼機控制項樣式，請指定左按鈕的 PGB_TOPORLEFT，然後 PGB_BOTTOMORRIGHT 右鍵按鈕。 如果有 PGS_VERT 的呼機控制項樣式，請針對上方按鈕指定 PGB_TOPORLEFT，然後針對底部按鈕指定 PGB_BOTTOMORRIGHT。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="return-value"></a>傳回值

如果指定的按鈕處於灰色狀態，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 的訊息，如 Windows SDK 中所述。 然後，它會測試傳回的狀態是否為 PGF_GRAYED。 如需詳細資訊，請參閱 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 訊息的傳回值一節。

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a> CPagerCtrl：： IsButtonHot

指出目前呼機控制項的指定滾動按鈕是否處於作用中狀態。

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>參數

*iButton*\
在表示要取得狀態的按鈕。 如果有 PGS_HORZ 的呼機控制項樣式，請指定左按鈕的 PGB_TOPORLEFT，然後 PGB_BOTTOMORRIGHT 右鍵按鈕。 如果有 PGS_VERT 的呼機控制項樣式，請針對上方按鈕指定 PGB_TOPORLEFT，然後針對底部按鈕指定 PGB_BOTTOMORRIGHT。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="return-value"></a>傳回值

如果指定的按鈕處於作用中狀態，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 的訊息，如 Windows SDK 中所述。 然後，它會測試傳回的狀態是否為 PGF_HOT。 如需詳細資訊，請參閱 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 訊息的傳回值一節。

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a> CPagerCtrl：： IsButtonInvisible

指出目前呼機控制項的指定滾動按鈕是否處於不可見狀態。

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>參數

*iButton*\
在表示要取得狀態的按鈕。 如果有 PGS_HORZ 的呼機控制項樣式，請指定左按鈕的 PGB_TOPORLEFT，然後 PGB_BOTTOMORRIGHT 右鍵按鈕。 如果有 PGS_VERT 的呼機控制項樣式，請針對上方按鈕指定 PGB_TOPORLEFT，然後針對底部按鈕指定 PGB_BOTTOMORRIGHT。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="return-value"></a>傳回值

如果指定的按鈕處於隱藏狀態，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當包含的視窗滾動至最遠的範圍時，Windows 會將滾動按鈕放在特定的方向，而不會將更多的內含視窗帶到最遠的範圍。

這個方法會傳送 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 的訊息，如 Windows SDK 中所述。 然後，它會測試傳回的狀態是否為 PGF_INVISIBLE。 如需詳細資訊，請參閱 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 訊息的傳回值一節。

### <a name="example"></a>範例

下列範例會使用 [CPagerCtrl：： IsButtonInvisible](#isbuttoninvisible) 方法來判斷是否可以看到頁面導航控制項的左邊和右邊滾動按鈕。

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a> CPagerCtrl：： IsButtonNormal

指出目前呼機控制項的指定滾動按鈕是否處於正常狀態。

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>參數

*iButton*\
在表示要取得狀態的按鈕。 如果有 PGS_HORZ 的呼機控制項樣式，請指定左按鈕的 PGB_TOPORLEFT，然後 PGB_BOTTOMORRIGHT 右鍵按鈕。 如果有 PGS_VERT 的呼機控制項樣式，請針對上方按鈕指定 PGB_TOPORLEFT，然後針對底部按鈕指定 PGB_BOTTOMORRIGHT。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="return-value"></a>傳回值

如果指定的按鈕處於正常狀態，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 的訊息，如 Windows SDK 中所述。 然後，它會測試傳回的狀態是否為 PGF_NORMAL。 如需詳細資訊，請參閱 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) 訊息的傳回值一節。

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a> CPagerCtrl：： RecalcSize

導致目前的頁面控制項重新計算包含視窗的大小。

```cpp
void RecalcSize();
```

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) 的訊息，如 Windows SDK 中所述。 因此，呼機控制項會傳送 [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) 通知，以取得所包含視窗的可滾動維度。

### <a name="example"></a>範例

下列範例會使用 [CPagerCtrl：： RecalcSize](#recalcsize) 方法來要求目前的呼機控制項重新計算其大小。

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>範例

下列範例會使用 [訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md) ，讓呼機控制項重新計算其本身的大小，而不需要控制項的父對話方塊來執行計算。 此範例會 `MyPagerCtrl` 從 [CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)衍生類別，然後使用訊息對應將 [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) 通知與 `OnCalcsize` 通知處理常式產生關聯。 在此範例中，通知處理常式會將分頁控制項的寬度和高度設定為固定值。

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a> CPagerCtrl：： SetBkColor

設定目前呼機控制項的背景色彩。

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>參數

*clrBk*\
在 [COLORREF](/windows/win32/gdi/colorref) 值，其中包含分頁控制項的新背景色彩。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值，其中包含頁面導航控制項的先前背景色彩。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用 [CPagerCtrl：： SetBkColor](#setbkcolor) 方法，將呼機控制項的背景色彩設定為紅色，並使用 [CPagerCtrl：： GetBkColor](#getbkcolor) 方法來確認是否已進行變更。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a> CPagerCtrl：： SetBorder

設定目前呼機控制項的框線大小。

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>參數

*iBorder*\
在新的框線大小（以圖元為單位）。 如果 *iBorder* 參數為負值，則框線大小會設定為零。

### <a name="return-value"></a>傳回值

先前的框線大小（以圖元為單位）。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會建立一個分頁控制項，然後使用 [CPagerCtrl：： SetChild](#setchild) 方法，將非常長的按鈕控制項與頁面控制項產生關聯。 然後，此範例會使用 [CPagerCtrl：： SetButtonSize](#setbuttonsize) 方法，將呼機控制項的高度設定為20圖元，並使用 [CPagerCtrl：： SetBorder](#setborder) 方法將框線粗細設定為1圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a> CPagerCtrl：： SetButtonSize

設定目前呼機控制項的按鈕大小。

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>參數

*iButtonSize*\
在新的按鈕大小（以圖元為單位）。

### <a name="return-value"></a>傳回值

先前的按鈕大小（以圖元為單位）。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) 的訊息，如 Windows SDK 中所述。

如果呼機控制項有 PGS_HORZ 樣式，則按鈕大小會決定頁面的寬度，而如果呼機控制項具有 PGS_VERT 樣式，則按鈕大小會決定頁面的高度。 預設按鈕大小是捲軸寬度的三 fourths，而最小按鈕大小為12圖元。 如需詳細資訊，請參閱 [呼機控制項樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="example"></a>範例

下列範例會建立一個分頁控制項，然後使用 [CPagerCtrl：： SetChild](#setchild) 方法，將非常長的按鈕控制項與頁面控制項產生關聯。 然後，此範例會使用 [CPagerCtrl：： SetButtonSize](#setbuttonsize) 方法，將呼機控制項的高度設定為20圖元，並使用 [CPagerCtrl：： SetBorder](#setborder) 方法將框線粗細設定為1圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a> CPagerCtrl：： SetChild

為目前的頁面控制項設定包含的視窗。

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>參數

*hwndChild*\
在要包含的視窗控制碼。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) 的訊息，如 Windows SDK 中所述。

這個方法不會變更包含視窗的父系;它只會將視窗控制碼指派給呼機控制項以供滾動。 在大部分的情況下，包含的視窗將會是分頁控制項的子視窗。

### <a name="example"></a>範例

下列範例會建立一個分頁控制項，然後使用 [CPagerCtrl：： SetChild](#setchild) 方法，將非常長的按鈕控制項與頁面控制項產生關聯。 然後，此範例會使用 [CPagerCtrl：： SetButtonSize](#setbuttonsize) 方法，將呼機控制項的高度設定為20圖元，並使用 [CPagerCtrl：： SetBorder](#setborder) 方法將框線粗細設定為1圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a> CPagerCtrl：： SetScrollPos

設定目前呼機控制項的滾動位置。

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>參數

*Ipo*\
在新的捲軸位置，以圖元為單位。

### <a name="remarks"></a>備註

這個方法會傳送 [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) 的訊息，如 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[呼機控制項](/windows/win32/Controls/pager-controls)
