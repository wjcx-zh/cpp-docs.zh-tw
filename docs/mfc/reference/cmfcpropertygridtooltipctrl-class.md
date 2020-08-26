---
title: CMFCPropertyGridToolTipCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 82d5f021204628121be242845583797348d02120
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840748"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 類別

實行 [CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md) 用來顯示工具提示的工具提示控制項。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|[CMFCPropertyGridToolTipCtrl：： CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|建構 `CMFCPropertyGridToolTipCtrl` 物件。|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCPropertyGridToolTipCtrl：： Create](#create)|建立工具提示控制項的視窗。|
|[CMFCPropertyGridToolTipCtrl：:D eactivate](#deactivate)|停用並隱藏工具提示控制項。|
|[CMFCPropertyGridToolTipCtrl：： GetLastRect](#getlastrect)|傳回工具提示控制項最後一個位置的座標。|
|[CMFCPropertyGridToolTipCtrl：： Hide](#hide)|隱藏工具提示控制項。|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式之前的視窗訊息。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCPropertyGridToolTipCtrl：： SetTextMargin](#settextmargin)|設定工具提示文字與工具提示視窗框線之間的間距。|
|[CMFCPropertyGridToolTipCtrl：： Track](#track)|顯示工具提示控制項。|

## <a name="remarks"></a>備註

當指標停留在屬性名稱上時，就會顯示工具提示。 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)類別會顯示工具提示，讓使用者可以輕鬆地讀取。 工具提示的位置通常取決於指標的位置。 使用這個類別時，工具提示會出現在屬性名稱上方，類似于自然屬性延伸，讓屬性名稱完全可見。

MFC 會自動建立這個控制項，並在 [CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)中使用它。

## <a name="example"></a>範例

下列範例示範如何建立類別的物件 `CMFCPropertyGridToolTipCtrl` ，以及如何顯示工具提示控制項。

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxpropertygridtooltipctrl。h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a> CMFCPropertyGridToolTipCtrl：： CMFCPropertyGridToolTipCtrl

建構 `CMFCPropertyGridToolTipCtrl` 物件。

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a> CMFCPropertyGridToolTipCtrl：： Create

建立工具提示控制項的視窗。

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
在父視窗的指標。

### <a name="return-value"></a>傳回值

如果已成功建立視窗，則為 TRUE;否則為 FALSE。

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a> CMFCPropertyGridToolTipCtrl：:D eactivate

停用並隱藏工具提示控制項。

```cpp
void Deactivate();
```

### <a name="remarks"></a>備註

這個方法會將最後一個位置和文字設定為空白值，以便未來對 [CMFCPropertyGridToolTipCtrl：： Track](#track) 的呼叫會顯示工具提示。

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a> CMFCPropertyGridToolTipCtrl：： GetLastRect

傳回工具提示控制項最後一個位置的座標。

```cpp
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

*矩形*<br/>
擴展包含工具提示控制項的最後一個位置。

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a> CMFCPropertyGridToolTipCtrl：： Hide

隱藏工具提示控制項。

```cpp
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a> CMFCPropertyGridToolTipCtrl：： SetTextMargin

設定工具提示文字與工具提示視窗框線之間的間距。

```cpp
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>參數

*nTextMargin*<br/>
在指定工具提示控制項文字與工具提示視窗框線之間的間距。 預設值為10圖元。

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a> CMFCPropertyGridToolTipCtrl：： Track

顯示工具提示控制項。

```cpp
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>參數

*矩形*<br/>
在指定工具提示控制項的位置和大小。

*strText*<br/>
在指定要顯示在工具提示中的文字。

### <a name="remarks"></a>備註

這個方法會在 *rect*指定的位置和大小中顯示工具提示控制項。 如果在上次呼叫這個方法之後，位置、大小和文字沒有變更，這個方法就不會有任何作用。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
