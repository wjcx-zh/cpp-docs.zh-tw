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
ms.openlocfilehash: 6c14ed1f11a7a414332b34566a314459d76b911b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303920"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl 類別

實作的工具提示控制項[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)用以顯示工具提示。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|建構 `CMFCPropertyGridToolTipCtrl` 物件。|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|建立工具提示控制項的視窗。|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|停用並隱藏工具提示控制項。|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|傳回工具提示控制項的最後一個位置的座標。|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|隱藏工具提示控制項。|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) 和 [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式之前的視窗訊息。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|設定工具提示文字與工具提示視窗的框線之間的間距。|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|顯示工具提示控制項。|

## <a name="remarks"></a>備註

當指標停留在屬性名稱時，會顯示工具提示。 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)類別會顯示工具提示，如此就可輕鬆閱讀的使用者。 工具提示的位置通常取決於指標的位置。 藉由使用這個類別，工具提示會出現在屬性名稱，類似自然的屬性延伸，以便完全顯示屬性名稱。

MFC 自動建立此控制項，並使用它在[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)。

## <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCPropertyGridToolTipCtrl`類別，以及如何顯示工具提示控制項。

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertygridtooltipctrl.h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

建構 `CMFCPropertyGridToolTipCtrl` 物件。

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

建立工具提示控制項的視窗。

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>參數

*pWndParent*<br/>
[in]父視窗的指標。

### <a name="return-value"></a>傳回值

如果視窗已成功建立，則為 TRUE否則為 FALSE。

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

停用並隱藏工具提示控制項。

```
void Deactivate();
```

### <a name="remarks"></a>備註

這個方法會設定的最後一個位置和文字為空值，以便未來呼叫[CMFCPropertyGridToolTipCtrl::Track](#track)顯示工具提示。

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

傳回工具提示控制項的最後一個位置的座標。

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>參數

*rect*<br/>
[out]包含工具提示控制項的最後一個位置。

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

隱藏工具提示控制項。

```
void Hide();
```

##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin

設定工具提示文字與工具提示視窗的框線之間的間距。

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>參數

*nTextMargin*<br/>
[in]指定的工具提示控制項的文字與工具提示視窗的框線之間的間距。 預設值是 10 個像素。

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

顯示工具提示控制項。

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>參數

*rect*<br/>
[in]指定的位置和大小的工具提示控制項。

*strText*<br/>
[in]指定要在工具提示中顯示的文字。

### <a name="remarks"></a>備註

這個方法會顯示工具提示控制項的位置與所指定的大小*rect*。 如果未呼叫此方法的上次變更位置、 大小和文字，則這個方法沒有任何作用。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
