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
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376158"
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
|[COle ResizeBar:COle resizebar](#coleresizebar)|建構 `COleResizeBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle Resize 列:建立](#create)|創建 Windows 子視窗並將其初始化,並將其`COleResizeBar`關聯到 物件。|

## <a name="remarks"></a>備註

`COleResizeBar`對象顯示為具有陰影邊框和外部調整大小的控點的[CRectTracker。](../../mfc/reference/crecttracker-class.md)

`COleResizeBar`物件通常是派生自[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)類的幀視窗物件的嵌入成員。

有關詳細資訊,請參閱文章[啟動](../../mfc/activation-cpp.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制列](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COle ResizeBar:COle resizebar

建構 `COleResizeBar` 物件。

```
COleResizeBar();
```

### <a name="remarks"></a>備註

呼叫`Create`以創建調整條形物件的大小。

## <a name="coleresizebarcreate"></a><a name="create"></a>COle Resize 列:建立

建立子視窗並將其與`COleResizeBar`物件關聯。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向調整大小條的父視窗。

*dwStyle*<br/>
指定[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)屬性。

*nID*<br/>
調整條形的子視窗 ID 的大小。

### <a name="return-value"></a>傳回值

如果創建了調整大小條,則非零;否則 0。

## <a name="see-also"></a>另請參閱

[MFC 樣品 SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc 類別](../../mfc/reference/coleserverdoc-class.md)
