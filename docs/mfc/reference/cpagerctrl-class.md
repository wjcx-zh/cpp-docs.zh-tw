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
ms.openlocfilehash: b2c4f1ac99735953f4832226b840ced4ea4c509a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376970"
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
|[CPagerCtrl:CPagerCtrl](#cpagerctrl)|建構 `CPagerCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPagerCtrl::創建](#create)|創建具有指定樣式的尋呼器控制程式並將其附加到當前`CPagerCtrl`物件。|
|[CPagerCtrl::創建Ex](#createex)|創建具有指定擴展樣式的尋呼器控制項,並將其附加到當前`CPagerCtrl`物件。|
|[CPagerCtrl::前進滑鼠](#forwardmouse)|啟用或禁用將[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)訊息轉發到當前尋呼器控制項中包含的視窗。|
|[CPagerCtrl:GetBkColor](#getbkcolor)|檢索目前尋呼器控制件的背景顏色。|
|[CPagerCtrl::取得邊界](#getborder)|檢索當前尋呼機控件的邊框大小。|
|[CPagerCtrl:取得按鈕大小](#getbuttonsize)|檢索目前尋呼機控件的按鈕大小。|
|[CPagerCtrl::取得按鈕狀態](#getbuttonstate)|檢索目前尋呼機控件中指定按鈕的狀態。|
|[CPagerCtrl::取得DropTarget](#getdroptarget)|檢索當前尋呼機控件的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)介面。|
|[CPagerCtrl::取得ScrollPos](#getscrollpos)|檢索當前尋呼器控件的滾動位置。|
|[CPagerCtrl::按壓鍵壓沉](#isbuttondepressed)|指示當前尋呼機控件的指定按鈕是否處於`pressed`狀態。|
|[CPagerCtrl::按鍵灰色](#isbuttongrayed)|指示當前尋呼機控件的指定按鈕是否處於`grayed`狀態。|
|[CPagerCtrl::是按鈕熱](#isbuttonhot)|指示當前尋呼機控件的指定按鈕是否處於`hot`狀態。|
|[CPagerCtrl::是按鈕不可見](#isbuttoninvisible)|指示當前尋呼機控件的指定按鈕是否處於`invisible`狀態。|
|[CPagerCtrl::正按鈕正常](#isbuttonnormal)|指示當前尋呼機控件的指定按鈕是否處於`normal`狀態。|
|[CPagerCtrl:recalcsize](#recalcsize)|使目前尋呼機控制件重新計算包含的視窗的大小。|
|[CPagerCtrl:setBkColor](#setbkcolor)|設置目前尋呼機控制件的背景顏色。|
|[CPagerCtrl::設定邊框](#setborder)|設置當前尋呼機控件的邊框大小。|
|[CPagerCtrl::設定按鈕大小](#setbuttonsize)|設置當前尋呼機控制件的按鈕大小。|
|[CPagerCtrl::SetChild](#setchild)|設置當前尋呼機控制件的包含視窗。|
|[CPagerCtrl::設定ScrollPos](#setscrollpos)|設置當前尋呼器控制件的滾動位置。|

## <a name="remarks"></a>備註

尋呼器控制項是一個視窗,其中包含另一個線性視窗,並且大於包含的視窗,並使您能夠將包含的視窗滾動到檢視中。 尋呼機控件顯示兩個滾動按鈕,當包含的視窗滾動到其最遠的範圍時,這些按鈕會自動消失,否則重新出現。 您可以建立水平或垂直滾動的尋呼器控制項。

例如,如果應用程式具有不夠寬的工具列來顯示其所有項,則可以將工具列分配給尋呼機控制項,並且使用者將能夠向左或向右滾動工具列以存取所有項。 微軟 IE 瀏覽器版本 4.0(commctrl.dll 版本 4.71)引入了尋呼機控制項。

類`CPagerCtrl`派生自[CWnd](../../mfc/reference/cwnd-class.md)類。 有關詳細資訊和尋呼器控制程式的外掛圖,請參閱[尋呼器控制程式](/windows/win32/Controls/pager-controls)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl:CPagerCtrl

建構 `CPagerCtrl` 物件。

```
CPagerCtrl();
```

### <a name="remarks"></a>備註

使用[CPagerCtrl::創建](#create)或[CPagerCtrl:createEx 方法](#createex)創建尋呼器控制`CPagerCtrl`件並將其附加到 物件。

## <a name="cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::創建

創建具有指定樣式的尋呼器控制程式並將其附加到當前`CPagerCtrl`物件。

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
|*dwStyle*|[在]要應用於控制[項的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)的位組合 (OR)。|
|*矩形*|[在]對包含客戶端座標中控制件的位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用。|
|*pparentwnd*|[在]指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該對像是控制項的父視窗。 此參數不可以是 NULL。|
|*nID*|[在]控件的識別碼。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

要創建尋呼器控制項,請聲明`CPagerCtrl`變數,然後調用[CPagerCtrl::創建](#create)或[CPagerCtrl::創建](#createex)該變數上的Ex方法。

### <a name="example"></a>範例

下面的示例創建尋呼器控制項,然後使用[CPagerCtrl:setChild](#setchild)方法將很長的按鈕控制件與尋呼機控制件相關聯。 然後,該示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法將尋呼機控制項的高度設定為 20 圖元,使用[CPagerCtrl:setBorder](#setborder)方法將邊框厚度設置為 1 圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::創建Ex

創建具有指定擴展樣式的尋呼器控制項,並將其附加到當前`CPagerCtrl`物件。

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
|*dwExStyle*|[在]要應用於控制的擴充樣式的位組合。 有關詳細資訊,請參閱[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函數的*dwExStyle*參數。|
|*dwStyle*|[在]要應用於控制[項的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)的位組合 (OR)。|
|*矩形*|[在]對包含客戶端座標中控制件的位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用。|
|*pparentwnd*|[在]指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該對像是控制項的父視窗。 此參數不可以是 NULL。|
|*nID*|[在]控件的識別碼。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

要創建尋呼器控制項,請聲明`CPagerCtrl`變數,然後調用[CPagerCtrl::創建](#create)或[CPagerCtrl::創建](#createex)該變數上的Ex方法。

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::前進滑鼠

啟用或禁用將[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)訊息轉發到當前尋呼器控制項中包含的視窗。

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*b 前進*|[在]TRUE 轉發滑鼠訊息,或 FALSE 不轉發滑鼠訊息。|

### <a name="remarks"></a>備註

此方法發送[PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse)消息,這在 Windows SDK 中介紹。

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::取得邊界

檢索當前尋呼機控件的邊框大小。

```
int GetBorder() const;
```

### <a name="return-value"></a>傳回值

當前邊框大小,以像素為單位。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBORDER](/windows/win32/Controls/pgm-getborder)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下面的示例使用[CPagerCtrl::getBorder](#getborder)方法檢索尋呼機控件邊框的厚度。

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl:GetBkColor

檢索目前尋呼器控制件的背景顏色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>傳回值

包含尋呼機控制件的目前背景顏色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下面的範例使用[CPagerCtrl::SetBkColor](#setbkcolor)方法將尋呼機控制項的背景顏色設定為紅色,[使用 CPagerCtrl::getBkColor](#getbkcolor)方法確認已進行更改。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl:取得按鈕大小

檢索目前尋呼機控件的按鈕大小。

```
int GetButtonSize() const;
```

### <a name="return-value"></a>傳回值

當前按鈕大小,以像素為單位。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize)消息,這在 Windows SDK 中介紹。

如果尋呼機控件具有PGS_HORZ樣式,則按鈕大小確定尋呼機按鈕的寬度,如果尋呼機控件具有PGS_VERT樣式,則按鈕大小將確定尋呼機按鈕的高度。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::取得按鈕狀態

檢索目前尋呼器控制項中指定滾動按鈕的狀態。

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[在]指示檢索狀態的按鈕。 如果尋呼機控制樣式PGS_HORZ,請為左鍵指定PGB_TOPORLEFT,併為右側按鈕指定PGB_BOTTOMORRIGHT。 如果尋呼機控制樣式為PGS_VERT,請為頂部按鈕指定PGB_TOPORLEFT,併為底部按鈕指定PGB_BOTTOMORRIGHT。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

*iButton*參數指定的按鈕的狀態。 狀態為PGF_INVISIBLE、PGF_NORMAL、PGF_GRAYED、PGF_DEPRESSED 或PGF_HOT。 有關詳細資訊,請參閱[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息,這在 Windows SDK 中介紹。

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::取得DropTarget

檢索當前尋呼機控件的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)介面。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>傳回值

指向當前尋呼`IDropTarget`機控件的介面的指標。

### <a name="remarks"></a>備註

`IDropTarget`是您為支援應用程式中的拖放操作而實現的介面之一。

此方法發送[PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget)消息,這在 Windows SDK 中介紹。 此方法的調用方負責在不再需要介面時調用`Release` [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)介面的成員。

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::取得ScrollPos

檢索當前尋呼器控件的滾動位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>傳回值

當前滾動位置,以像素為單位測量。

### <a name="remarks"></a>備註

此方法發送[PGM_GETPOS](/windows/win32/Controls/pgm-getpos)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下面的示例使用[CPagerCtrl::getScrollPos](#getscrollpos)方法檢索尋呼機控制項的當前滾動位置。 如果尋呼機控件尚未滾動到零,則該示例使用[CPagerCtrl::setScrollPos](#setscrollpos)方法將滾動位置設置為零。

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::按壓鍵壓沉

指示當前尋呼機控件的指定滾動按鈕是否處於按下狀態。

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[在]指示檢索狀態的按鈕。 如果尋呼機控制樣式PGS_HORZ,請為左鍵指定PGB_TOPORLEFT,併為右側按鈕指定PGB_BOTTOMORRIGHT。 如果尋呼機控制樣式為PGS_VERT,請為頂部按鈕指定PGB_TOPORLEFT,併為底部按鈕指定PGB_BOTTOMORRIGHT。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於按下狀態,則為 TRUE;如果指定的按鈕處於按下狀態。<否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息,這在 Windows SDK 中介紹。 然後,它將測試返回的狀態是否PGF_DEPRESSED。 有關詳細資訊,請參閱[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::按鍵灰色

指示當前尋呼機控件的指定滾動按鈕是否處於灰色狀態。

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[在]指示檢索狀態的按鈕。 如果尋呼機控制樣式PGS_HORZ,請為左鍵指定PGB_TOPORLEFT,併為右側按鈕指定PGB_BOTTOMORRIGHT。 如果尋呼機控制樣式為PGS_VERT,請為頂部按鈕指定PGB_TOPORLEFT,併為底部按鈕指定PGB_BOTTOMORRIGHT。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於灰色狀態,則為 TRUE;如果指定的按鈕處於灰色狀態。<否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息,這在 Windows SDK 中介紹。 然後,它將測試返回的狀態是否PGF_GRAYED。 有關詳細資訊,請參閱[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::是按鈕熱

指示當前尋呼機控件的指定滾動按鈕是否處於熱狀態。

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[在]指示檢索狀態的按鈕。 如果尋呼機控制樣式PGS_HORZ,請為左鍵指定PGB_TOPORLEFT,併為右側按鈕指定PGB_BOTTOMORRIGHT。 如果尋呼機控制樣式為PGS_VERT,請為頂部按鈕指定PGB_TOPORLEFT,併為底部按鈕指定PGB_BOTTOMORRIGHT。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於熱狀態,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息,這在 Windows SDK 中介紹。 然後,它將測試返回的狀態是否PGF_HOT。 有關詳細資訊,請參閱[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::是按鈕不可見

指示當前尋呼機控件的指定滾動按鈕是否處於不可見狀態。

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[在]指示檢索狀態的按鈕。 如果尋呼機控制樣式PGS_HORZ,請為左鍵指定PGB_TOPORLEFT,併為右側按鈕指定PGB_BOTTOMORRIGHT。 如果尋呼機控制樣式為PGS_VERT,請為頂部按鈕指定PGB_TOPORLEFT,併為底部按鈕指定PGB_BOTTOMORRIGHT。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於不可見狀態,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

當包含的視窗滾動到最遠的範圍時,Windows 使特定方向的滾動按鈕不可見,因為進一步單擊該按鈕無法將更多包含的視窗帶入視圖。

此方法發送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息,這在 Windows SDK 中介紹。 然後,它將測試返回的狀態是否PGF_INVISIBLE。 有關詳細資訊,請參閱[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

### <a name="example"></a>範例

下面的示例使用[CPagerCtrl::isButton 不可見](#isbuttoninvisible)方法來確定尋呼機控制件的左右滾動按鈕是否可見。

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::正按鈕正常

指示當前尋呼機控件的指定滾動按鈕是否處於正常狀態。

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButton*|[在]指示檢索狀態的按鈕。 如果尋呼機控制樣式PGS_HORZ,請為左鍵指定PGB_TOPORLEFT,併為右側按鈕指定PGB_BOTTOMORRIGHT。 如果尋呼機控制樣式為PGS_VERT,請為頂部按鈕指定PGB_TOPORLEFT,併為底部按鈕指定PGB_BOTTOMORRIGHT。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>傳回值

如果指定的按鈕處於正常狀態,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息,這在 Windows SDK 中介紹。 然後,它將測試返回的狀態是否PGF_NORMAL。 有關詳細資訊,請參閱[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl:recalcsize

使目前尋呼機控制件重新計算包含的視窗的大小。

```
void RecalcSize();
```

### <a name="remarks"></a>備註

此方法發送[PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize)訊息,這在 Windows SDK 中介紹。 因此,尋呼機控件發送[PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知以獲取包含視窗的可滾動維度。

### <a name="example"></a>範例

下面的示例使用[CPagerCtrl::recalcsize](#recalcsize)方法請求當前尋呼機控制項重新計算其大小。

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>範例

下面的示例使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)使尋呼機控件能夠重新計算其自身大小,而不是要求控制項的父對話框執行計算。 該示例從`MyPagerCtrl`[CPagerCtrl 類](../../mfc/reference/cpagerctrl-class.md)派生類,然後使用消息映射將[PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知與`OnCalcsize`通知處理程序相關聯。 在此示例中,通知處理程式將尋呼機控件的寬度和高度設置為固定值。

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl:setBkColor

設置目前尋呼機控制件的背景顏色。

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*clrBk*|[在]包含尋呼機控制元件的新背景顏色的[COLORREF](/windows/win32/gdi/colorref)值。|

### <a name="return-value"></a>傳回值

包含尋呼機控制件的上一個背景顏色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

此方法發送[PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下面的範例使用[CPagerCtrl::SetBkColor](#setbkcolor)方法將尋呼機控制項的背景顏色設定為紅色,[使用 CPagerCtrl::getBkColor](#getbkcolor)方法確認已進行更改。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::設定邊框

設置當前尋呼機控件的邊框大小。

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iBorder*|[在]新的邊框大小,以像素為單位。 如果*iBorder*參數為負,則邊框大小設置為零。|

### <a name="return-value"></a>傳回值

以前的邊框大小,以像素為單位。

### <a name="remarks"></a>備註

此方法發送[PGM_SETBORDER](/windows/win32/Controls/pgm-setborder)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

下面的示例創建尋呼器控制項,然後使用[CPagerCtrl:setChild](#setchild)方法將很長的按鈕控制件與尋呼機控制件相關聯。 然後,該示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法將尋呼機控制項的高度設定為 20 圖元,使用[CPagerCtrl:setBorder](#setborder)方法將邊框厚度設置為 1 圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::設定按鈕大小

設置當前尋呼機控制件的按鈕大小。

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iButtonSize*|[在]新的按鈕大小,以像素為單位。|

### <a name="return-value"></a>傳回值

以前的按鈕大小,以像素為單位。

### <a name="remarks"></a>備註

此方法發送[PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos)消息,這在 Windows SDK 中介紹。

如果尋呼機控件具有PGS_HORZ樣式,則按鈕大小確定尋呼機按鈕的寬度,如果尋呼機控件具有PGS_VERT樣式,則按鈕大小將確定尋呼機按鈕的高度。 默認按鈕大小是滾動條寬度的四分之三,最小按鈕大小為 12 圖元。 有關詳細資訊,請參閱[尋呼器控制樣式](/windows/win32/Controls/pager-control-styles)。

### <a name="example"></a>範例

下面的示例創建尋呼器控制項,然後使用[CPagerCtrl:setChild](#setchild)方法將很長的按鈕控制件與尋呼機控制件相關聯。 然後,該示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法將尋呼機控制項的高度設定為 20 圖元,使用[CPagerCtrl:setBorder](#setborder)方法將邊框厚度設置為 1 圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild

設置當前尋呼機控制件的包含視窗。

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*霍恩德兒童*|[在]句柄要包含的視窗。|

### <a name="remarks"></a>備註

此方法發送[PGM_SETCHILD](/windows/win32/Controls/pgm-setchild)消息,這在 Windows SDK 中介紹。

此方法不變更包含視窗的父級,因此不改變它僅將視窗句柄分配給尋呼機控件進行滾動。 在大多數情況下,包含的視窗將是尋呼機控件的子視窗。

### <a name="example"></a>範例

下面的示例創建尋呼器控制項,然後使用[CPagerCtrl:setChild](#setchild)方法將很長的按鈕控制件與尋呼機控制件相關聯。 然後,該示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法將尋呼機控制項的高度設定為 20 圖元,使用[CPagerCtrl:setBorder](#setborder)方法將邊框厚度設置為 1 圖元。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::設定ScrollPos

設置當前尋呼器控制件的滾動位置。

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Ipo*|[在]新的滾動位置,以像素為單位。|

### <a name="remarks"></a>備註

此方法發送[PGM_SETPOS](/windows/win32/Controls/pgm-setpos)消息,這在 Windows SDK 中介紹。

## <a name="see-also"></a>另請參閱

[CPagerCtrl 類別](../../mfc/reference/cpagerctrl-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[呼叫器控制項](/windows/win32/Controls/pager-controls)
