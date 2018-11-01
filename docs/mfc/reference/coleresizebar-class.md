---
title: COleResizeBar 類別
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: c4b7ce80762cdb49b6007eac7f6b26019b108795
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445106"
---
# <a name="coleresizebar-class"></a>COleResizeBar 類別

支援就地 OLE 項目調整大小的控制列類型。

## <a name="syntax"></a>語法

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|建構 `COleResizeBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleResizeBar::Create](#create)|建立並初始化 Windows 子視窗，並將它`COleResizeBar`物件。|

## <a name="remarks"></a>備註

`COleResizeBar` 物件會顯示為[CRectTracker](../../mfc/reference/crecttracker-class.md)具有陰影的框線和外部調整大小控點。

`COleResizeBar` 物件是衍生自的框架視窗物件通常是內嵌的成員[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)類別。

如需詳細資訊，請參閱文章[啟用](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar

建構 `COleResizeBar` 物件。

```
COleResizeBar();
```

### <a name="remarks"></a>備註

呼叫`Create`建立調整列物件。

##  <a name="create"></a>  COleResizeBar::Create

建立子視窗，並將其與相關聯`COleResizeBar`物件。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
大小調整列的父視窗的指標。

*cheaderctrl:: Create*<br/>
指定[styl okna](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。

*nID*<br/>
大小調整列的子視窗識別碼。

### <a name="return-value"></a>傳回值

非零值，如果已建立的大小調整列;否則為 0。

## <a name="see-also"></a>另請參閱

[MFC 範例 SUPERPAD](../../visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)
