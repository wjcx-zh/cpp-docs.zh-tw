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
ms.openlocfilehash: fc5d6d99c326fba7020e8c5040c3bf28d09f8f0a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754124"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 類別

實現[CMFCPropertyGridCtrl 類](../../mfc/reference/cmfcpropertygridctrl-class.md)用於顯示工具提示的工具提示控制項。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFC 屬性網格工具提示::CMFC 屬性網格工具提示rl](#cmfcpropertygridtooltipctrl)|建構 `CMFCPropertyGridToolTipCtrl` 物件。|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC 屬性網格工具提示::建立](#create)|為工具提示控制項製作一個視窗。|
|[CMFC 屬性網格工具提示::D啟動](#deactivate)|停用並隱藏工具提示控制項。|
|[CMFC財產網格工具提示::獲取最後](#getlastrect)|傳回工具提示控制項最後一個位置的座標。|
|[CMFC 屬性網格工具提示::隱藏](#hide)|隱藏工具提示控制項。|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式之前的視窗訊息。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFC 屬性網格工具提示::設定文字邊緣](#settextmargin)|設定工具提示文本與工具提示視窗邊框之間的間距。|
|[CMFC財產網格工具提示::軌道](#track)|顯示工具提示控制項。|

## <a name="remarks"></a>備註

當指標位於屬性名稱上時,將顯示工具提示。 [CMFC屬性GridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)類顯示一個工具提示,以便用戶可以輕鬆閱讀。 通常,工具提示的位置由指標的位置決定。 通過使用此類,工具提示將顯示在屬性名稱上,類似於自然屬性擴展,因此屬性名稱完全可見。

MFC 會自動建立此控制項,並在[CMFC 屬性格格 Ctrl 類](../../mfc/reference/cmfcpropertygridctrl-class.md)中使用它。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCPropertyGridToolTipCtrl`類的物件以及如何顯示工具提示控制項。

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFC 財產網格工具提示器](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afx屬性網格tooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFC 屬性網格工具提示::CMFC 屬性網格工具提示rl

建構 `CMFCPropertyGridToolTipCtrl` 物件。

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFC 屬性網格工具提示::建立

為工具提示控制項製作一個視窗。

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
[在]指向父視窗的指標。

### <a name="return-value"></a>傳回值

如果成功創建視窗,則為 TRUE;如果成功創建了視窗,則為 TRUE。否則,FALSE。

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFC 屬性網格工具提示::D啟動

停用並隱藏工具提示控制項。

```cpp
void Deactivate();
```

### <a name="remarks"></a>備註

此方法將最後一個位置和文本設置為空值,以便將來對[CMFC 屬性網格ToolTipCtrl的調用:跟蹤](#track)顯示工具提示。

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFC財產網格工具提示::獲取最後

傳回工具提示控制項最後一個位置的座標。

```cpp
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

*矩形*<br/>
[出]包含工具提示控制項的最後位置。

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFC 屬性網格工具提示::隱藏

隱藏工具提示控制項。

```cpp
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFC 屬性網格工具提示::設定文字邊緣

設定工具提示文本與工具提示視窗邊框之間的間距。

```cpp
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>參數

*nTextMargin*<br/>
[在]指定工具提示控制項文字與工具提示視窗的邊框之間的間距。 默認值為 10 圖元。

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFC財產網格工具提示::軌道

顯示工具提示控制項。

```cpp
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>參數

*矩形*<br/>
[在]指定工具提示控制項的位置和大小。

*斯特文字*<br/>
[在]指定要在工具提示中顯示的文字。

### <a name="remarks"></a>備註

此方法在*rect*指定的位置和大小處顯示工具提示控制項。 如果自上次調用此方法以來位置、大小和文本未更改,則此方法沒有效果。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
