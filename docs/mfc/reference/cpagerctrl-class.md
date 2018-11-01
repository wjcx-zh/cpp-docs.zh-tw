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
ms.openlocfilehash: cd3eed89753031de64d35a2b3602b1fb42356123
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613534"
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
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|建構 `CPagerCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|使用指定的樣式中建立之頁面巡覽控制項，並將它附加至目前`CPagerCtrl`物件。|
|[CPagerCtrl::CreateEx](#createex)|使用指定的延伸樣式中建立之頁面巡覽控制項，並將它附加至目前`CPagerCtrl`物件。|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|啟用或停用轉寄[WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove)包含在目前的頁面巡覽區控制項的視窗訊息。|
|[CPagerCtrl::GetBkColor](#getbkcolor)|擷取目前的頁面巡覽區控制項的背景色彩。|
|[CPagerCtrl::GetBorder](#getborder)|擷取目前的頁面巡覽控制項的框線大小。|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|擷取目前的頁面巡覽控制項的按鈕大小。|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|擷取指定的按鈕，在目前的頁面巡覽區控制項的狀態。|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|擷取[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)目前的頁面巡覽區控制項的介面。|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|擷取目前的頁面巡覽控制項的捲動位置。|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|指出是否在指定目前的頁面巡覽控制項的按鈕`pressed`狀態。|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|指出是否在指定目前的頁面巡覽控制項的按鈕`grayed`狀態。|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|指出是否在指定目前的頁面巡覽控制項的按鈕`hot`狀態。|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|指出是否在指定目前的頁面巡覽控制項的按鈕`invisible`狀態。|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|指出是否在指定目前的頁面巡覽控制項的按鈕`normal`狀態。|
|[CPagerCtrl::RecalcSize](#recalcsize)|使目前的頁面巡覽區控制項重新計算包含視窗的大小。|
|[CPagerCtrl::SetBkColor](#setbkcolor)|設定目前的頁面巡覽控制項的背景色彩。|
|[CPagerCtrl::SetBorder](#setborder)|設定目前的頁面巡覽控制項的框線大小。|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|設定目前的頁面巡覽控制項的按鈕大小。|
|[CPagerCtrl::SetChild](#setchild)|設定目前的頁面巡覽區控制項的自主的視窗。|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|設定目前的頁面巡覽控制項的捲動位置。|

## <a name="remarks"></a>備註

頁面巡覽區控制項是包含另一個視窗中，是線性且大於所包含的視窗，可讓您在包含的視窗捲動至檢視的視窗。 頁面巡覽區控制項顯示自動消失時包含的視窗捲動，其最遠的範圍內的兩個捲軸按鈕，並重新顯示否則。 您可以建立水平或垂直捲動的頁面巡覽區控制項。

比方說，如果您的應用程式有一個工具列，寬度不夠，無法顯示所有的項目，您可以指派至頁面巡覽區控制項的工具列和使用者能夠捲動至左方或右方，若要存取的所有項目工具列。 Microsoft Internet Explorer 版本 4.0 （commctrl.dll 版本 4.71） 導入了頁面巡覽區控制項。

`CPagerCtrl`類別衍生自[CWnd](../../mfc/reference/cwnd-class.md)類別。 如需詳細資訊和頁面巡覽控制項的說明，請參閱[呼叫器控制項](/windows/desktop/Controls/pager-controls)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl

建構 `CPagerCtrl` 物件。

```
CPagerCtrl();
```

### <a name="remarks"></a>備註

使用[CPagerCtrl::Create](#create)或是[CPagerCtrl::CreateEx](#createex)方法來建立頁面巡覽區控制項，並將其附加至`CPagerCtrl`物件。

##  <a name="create"></a>  CPagerCtrl::Create

使用指定的樣式中建立之頁面巡覽控制項，並將它附加至目前`CPagerCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*cheaderctrl:: Create*|[in]位元組合 (OR)[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)並[頁面巡覽區控制項的樣式](/windows/desktop/Controls/pager-control-styles)来套用至控制項。|
|*rect*|[in]參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含的位置和大小的工作區座標中的控制項。|
|*pParentWnd*|[in]指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。 這個參數不能是 NULL。|
|*nID*|[in]控制項的 ID。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

若要建立之頁面巡覽控制項，宣告`CPagerCtrl`變數，然後呼叫[CPagerCtrl::Create](#create)或是[CPagerCtrl::CreateEx](#createex)該變數上的方法。

### <a name="example"></a>範例

下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)很長的按鈕控制項相關聯的頁面巡覽區控制項的方法。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素的框線粗細。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>  CPagerCtrl::CreateEx

使用指定的延伸樣式中建立之頁面巡覽控制項，並將它附加至目前`CPagerCtrl`物件。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwExStyle*|[in]要套用至控制項的延伸樣式的位元組合。 如需詳細資訊，請參閱 < *dwExStyle*的參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)函式。|
|*cheaderctrl:: Create*|[in]位元組合 (OR)[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)並[頁面巡覽區控制項的樣式](/windows/desktop/Controls/pager-control-styles)来套用至控制項。|
|*rect*|[in]參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含的位置和大小的工作區座標中的控制項。|
|*pParentWnd*|[in]指標[CWnd](../../mfc/reference/cwnd-class.md)是控制項的父視窗的物件。 這個參數不能是 NULL。|
|*nID*|[in]控制項的 ID。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

若要建立之頁面巡覽控制項，宣告`CPagerCtrl`變數，然後呼叫[CPagerCtrl::Create](#create)或是[CPagerCtrl::CreateEx](#createex)該變數上的方法。

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

啟用或停用轉寄[WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove)包含在目前的頁面巡覽區控制項的視窗訊息。

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*bForward*|[in]True 表示正向的滑鼠訊息時傳回 FALSE 不將滑鼠訊息轉送。|

### <a name="remarks"></a>備註

這個方法會傳送[PGM_FORWARDMOUSE](/windows/desktop/Controls/pgm-forwardmouse)訊息，Windows SDK 中所述。

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

擷取目前的頁面巡覽控制項的框線大小。

```
int GetBorder() const;
```

### <a name="return-value"></a>傳回值

目前的框線大小，以像素表示。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBORDER](/windows/desktop/Controls/pgm-getborder)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用[CPagerCtrl::GetBorder](#getborder)方法來擷取頁面巡覽區控制項的框線粗細。

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

擷取目前的頁面巡覽區控制項的背景色彩。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)值，包含頁面巡覽控制項的目前的背景色彩。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBKCOLOR](/windows/desktop/Controls/pgm-getbkcolor)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用[CPagerCtrl::SetBkColor](#setbkcolor)方法來設定頁面巡覽區控制項的背景色彩為紅色，而[CPagerCtrl::GetBkColor](#getbkcolor)方法，以確認已進行變更。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize

擷取目前的頁面巡覽控制項的按鈕大小。

```
int GetButtonSize() const;
```

### <a name="return-value"></a>傳回值

目前的按鈕大小，以像素表示。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBUTTONSIZE](/windows/desktop/Controls/pgm-getbuttonsize)訊息，Windows SDK 中所述。

如果頁面巡覽區控制項有 PGS_HORZ 樣式，按鈕大小會決定頁面巡覽區按鈕的寬度和頁面巡覽區控制項有 PGS_VERT 樣式，按鈕大小會決定頁面巡覽區按鈕的高度。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

擷取目前的頁面巡覽區控制項中的指定捲軸按鈕的狀態。

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[in]表示要擷取狀態的按鈕。 PGS_HORZ 頁面巡覽區控制項樣式時，指定左的按鈕和 PGB_BOTTOMORRIGHT PGB_TOPORLEFT 右邊的按鈕。 PGS_VERT 頁面巡覽區控制項樣式時，指定 PGB_TOPORLEFT 頂端按鈕和 PGB_BOTTOMORRIGHT 底端按鈕。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

指定按鈕的狀態*iButton*參數。 狀態是 PGF_INVISIBLE、 PGF_NORMAL、 PGF_GRAYED、 PGF_DEPRESSED，或是 PGF_HOT。 如需詳細資訊，請參閱的傳回值區段[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息，Windows SDK 中所述。

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

擷取[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)目前的頁面巡覽區控制項的介面。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>傳回值

指標`IDropTarget`目前的頁面巡覽區控制項的介面。

### <a name="remarks"></a>備註

`IDropTarget` 是其中一個您要實作的介面，在您的應用程式支援拖放作業。

這個方法會傳送[PGM_GETDROPTARGET](/windows/desktop/Controls/pgm-getdroptarget)訊息，Windows SDK 中所述。 此方法的呼叫端會負責呼叫`Release`隸屬[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)介面時不再需要的介面。

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

擷取目前的頁面巡覽控制項的捲動位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>傳回值

目前的捲動位置，以像素表示。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETPOS](/windows/desktop/Controls/pgm-getpos)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用[CPagerCtrl::GetScrollPos](#getscrollpos)方法來擷取目前捲動位置的頁面巡覽區控制項。 如果為零，最左邊的位置，已經不捲動頁面巡覽區控制項的範例會使用[CPagerCtrl::SetScrollPos](#setscrollpos)方法，以將捲軸位置設定為零。

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

指出目前的頁面巡覽控制項的指定捲軸按鈕處於已按下狀態。

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[in]表示要擷取狀態的按鈕。 PGS_HORZ 頁面巡覽區控制項樣式時，指定左的按鈕和 PGB_BOTTOMORRIGHT PGB_TOPORLEFT 右邊的按鈕。 PGS_VERT 頁面巡覽區控制項樣式時，指定 PGB_TOPORLEFT 頂端按鈕和 PGB_BOTTOMORRIGHT 底端按鈕。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕是處於已按下狀態;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息，Windows SDK 中所述。 然後它會測試是否會傳回狀態為 PGF_DEPRESSED。 如需詳細資訊，請參閱的傳回值區段[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息。

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

指出目前的頁面巡覽控制項的指定捲軸按鈕是否為灰色的狀態。

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[in]表示要擷取狀態的按鈕。 PGS_HORZ 頁面巡覽區控制項樣式時，指定左的按鈕和 PGB_BOTTOMORRIGHT PGB_TOPORLEFT 右邊的按鈕。 PGS_VERT 頁面巡覽區控制項樣式時，指定 PGB_TOPORLEFT 頂端按鈕和 PGB_BOTTOMORRIGHT 底端按鈕。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕呈現灰色狀態;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息，Windows SDK 中所述。 然後它會測試是否會傳回狀態為 PGF_GRAYED。 如需詳細資訊，請參閱的傳回值區段[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息。

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

指出目前的頁面巡覽控制項的指定捲軸按鈕處於作用中狀態。

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[in]表示要擷取狀態的按鈕。 PGS_HORZ 頁面巡覽區控制項樣式時，指定左的按鈕和 PGB_BOTTOMORRIGHT PGB_TOPORLEFT 右邊的按鈕。 PGS_VERT 頁面巡覽區控制項樣式時，指定 PGB_TOPORLEFT 頂端按鈕和 PGB_BOTTOMORRIGHT 底端按鈕。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於作用中狀態，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息，Windows SDK 中所述。 然後它會測試是否會傳回狀態為 PGF_HOT。 如需詳細資訊，請參閱的傳回值區段[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息。

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

指出目前的頁面巡覽控制項的指定捲軸按鈕處於隱藏狀態。

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[in]表示要擷取狀態的按鈕。 PGS_HORZ 頁面巡覽區控制項樣式時，指定左的按鈕和 PGB_BOTTOMORRIGHT PGB_TOPORLEFT 右邊的按鈕。 PGS_VERT 頁面巡覽區控制項樣式時，指定 PGB_TOPORLEFT 頂端按鈕和 PGB_BOTTOMORRIGHT 底端按鈕。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於隱藏狀態，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

Windows 可讓捲軸按鈕依特定方向不可見時按一下按鈕進一步無法帶入多個包含視窗的檢視，因為包含的視窗捲動到其最遠的範圍。

這個方法會傳送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息，Windows SDK 中所述。 然後它會測試是否會傳回狀態為 PGF_INVISIBLE。 如需詳細資訊，請參閱的傳回值區段[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息。

### <a name="example"></a>範例

下列範例會使用[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)方法，以判斷是否頁面巡覽區控制項左邊緣與右捲動按鈕會顯示。

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

指出目前的頁面巡覽控制項的指定捲軸按鈕處於正常狀態。

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[in]表示要擷取狀態的按鈕。 PGS_HORZ 頁面巡覽區控制項樣式時，指定左的按鈕和 PGB_BOTTOMORRIGHT PGB_TOPORLEFT 右邊的按鈕。 PGS_VERT 頁面巡覽區控制項樣式時，指定 PGB_TOPORLEFT 頂端按鈕和 PGB_BOTTOMORRIGHT 底端按鈕。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於正常狀態，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息，Windows SDK 中所述。 然後它會測試是否會傳回狀態為 PGF_NORMAL。 如需詳細資訊，請參閱的傳回值區段[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)訊息。

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

使目前的頁面巡覽區控制項重新計算包含視窗的大小。

```
void RecalcSize();
```

### <a name="remarks"></a>備註

這個方法會傳送[PGM_RECALCSIZE](/windows/desktop/Controls/pgm-recalcsize)訊息，Windows SDK 中所述。 因此，會傳送頁面巡覽區控制項[PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize)通知，以取得包含視窗的可捲動的維度。

### <a name="example"></a>範例

下列範例會使用[CPagerCtrl::RecalcSize](#recalcsize)方法來要求重新計算其大小目前的頁面巡覽區控制項。

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>範例

下列範例會使用[訊息反映](../../mfc/tn062-message-reflection-for-windows-controls.md)以便重新計算它自己的大小，而不需要執行計算的控制項的父對話方塊的頁面巡覽區控制項。 範例衍生`MyPagerCtrl`類別從[CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)，然後用以建立關聯的訊息對應[PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize)通知`OnCalcsize`通知處理常式。 在此範例中，通知處理常式會設定頁面巡覽控制項的高度與寬度為固定值。

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

設定目前的頁面巡覽控制項的背景色彩。

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*clrBk*|[in]A [COLORREF](/windows/desktop/gdi/colorref)值，包含頁面巡覽控制項的新的背景色彩。|

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)值，包含前一個頁面巡覽控制項的背景色彩。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_SETBKCOLOR](/windows/desktop/Controls/pgm-setbkcolor)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會使用[CPagerCtrl::SetBkColor](#setbkcolor)方法來設定頁面巡覽區控制項的背景色彩為紅色，而[CPagerCtrl::GetBkColor](#getbkcolor)方法，以確認已進行變更。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

設定目前的頁面巡覽控制項的框線大小。

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iBorder*|[in]新的框線大小，以像素表示。 如果*iBorder*參數是負值，框線大小會設為零。|

### <a name="return-value"></a>傳回值

先前的框線大小，以像素表示。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_SETBORDER](/windows/desktop/Controls/pgm-setborder)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)很長的按鈕控制項相關聯的頁面巡覽區控制項的方法。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素的框線粗細。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

設定目前的頁面巡覽控制項的按鈕大小。

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButtonSize*|[in]新的按鈕大小，以像素表示。|

### <a name="return-value"></a>傳回值

先前的按鈕大小，以像素表示。

### <a name="remarks"></a>備註

這個方法會傳送[PGM_SETBUTTONSIZE](/windows/desktop/Controls/pgm-setpos)訊息，Windows SDK 中所述。

如果頁面巡覽區控制項有 PGS_HORZ 樣式，按鈕大小會決定頁面巡覽區按鈕的寬度和頁面巡覽區控制項有 PGS_VERT 樣式，按鈕大小會決定頁面巡覽區按鈕的高度。 預設按鈕的大小是四分之三的捲軸的寬度，而最小的按鈕大小為 12 個像素。 如需詳細資訊，請參閱 <<c0> [ 呼叫器控制項樣式](/windows/desktop/Controls/pager-control-styles)。

### <a name="example"></a>範例

下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)很長的按鈕控制項相關聯的頁面巡覽區控制項的方法。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素的框線粗細。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

設定目前的頁面巡覽區控制項的自主的視窗。

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*hwndChild*|[in]要包含視窗控制代碼。|

### <a name="remarks"></a>備註

這個方法會傳送[PGM_SETCHILD](/windows/desktop/Controls/pgm-setchild)訊息，Windows SDK 中所述。

這個方法不會變更父代包含的視窗;它只會指派給捲動的頁面巡覽區控制項的視窗控制代碼。 在大部分情況下，包含的視窗將會頁面巡覽控制項的子視窗。

### <a name="example"></a>範例

下列範例會建立頁面巡覽區控制項，則會使用[CPagerCtrl::SetChild](#setchild)很長的按鈕控制項相關聯的頁面巡覽區控制項的方法。 然後此範例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法，以將頁面巡覽控制項的高度設為 20 像素，而[CPagerCtrl::SetBorder](#setborder)方法設為 1 個像素的框線粗細。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

設定目前的頁面巡覽控制項的捲動位置。

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iPos*|[in]新的捲動位置，以像素表示。|

### <a name="remarks"></a>備註

這個方法會傳送[PGM_SETPOS](/windows/desktop/Controls/pgm-setpos)訊息，Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[頁面巡覽區控制項](/windows/desktop/Controls/pager-controls)

