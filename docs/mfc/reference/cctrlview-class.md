---
title: CCtrlView 類別
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: f77f1c265920bd160da790647ef754c55e6dbda3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369349"
---
# <a name="cctrlview-class"></a>CCtrlView 類別

調整文件檢視架構來配合 Windows 98 和 Windows NT 3.51 版 (含) 以後版本支援的通用控制項。

## <a name="syntax"></a>語法

```
class CCtrlView : public CView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CtrlView:CtrlView](#cctrlview)|建構 `CCtrlView` 物件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CtrlView:在畫上](#ondraw)|由框架調用,以便使用指定的設備上下文進行繪製。|
|[CtrlView::P重新建立視窗](#precreatewindow)|在建立附加至此 `CCtrlView` 物件的 Windows 視窗前呼叫。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CtrlView:m_dwDefaultStyle](#m_dwdefaultstyle)|包含檢視類的預設樣式。|
|[CtrlView:m_strClass](#m_strclass)|包含視圖類的 Windows 類名稱。|

## <a name="remarks"></a>備註

該類`CCtrlView`及其衍生工具 CEditView、CListView、CTreeView 和[CRichEditView](../../mfc/reference/cricheditview-class.md)使文檔視圖體系結構適應 Windows 95/98 和 Windows NT 版本[CEditView](../../mfc/reference/ceditview-class.md)[CListView](../../mfc/reference/clistview-class.md)[CTreeView](../../mfc/reference/ctreeview-class.md)3.51 及更高版本支援的新通用控制項。 有關文件檢視體系結構的詳細資訊,請參閱[文件/檢視體系結構](../../mfc/document-view-architecture.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a>CtrlView:CtrlView

建構 `CCtrlView` 物件。

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>參數

*lpszClass*<br/>
視圖類的 Windows 類名稱。

*dwStyle*<br/>
視圖類的樣式。

### <a name="remarks"></a>備註

創建新幀視窗或拆分視窗時,框架將調用構造函數。 覆蓋[CView::在附加](../../mfc/reference/cview-class.md#oninitialupdate)文件後初始化檢視的「初始更新」。 調用[CWnd::創建](../../mfc/reference/cwnd-class.md#create)或[CWnd:創建Ex](../../mfc/reference/cwnd-class.md#createex)以創建 Windows 物件。

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a>CtrlView:m_strClass

包含視圖類的 Windows 類名稱。

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CtrlView:m_dwDefaultStyle

包含檢視類的預設樣式。

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>備註

建立視窗時應用此樣式。

## <a name="cctrlviewondraw"></a><a name="ondraw"></a>CtrlView:在畫上

由框架呼叫,以便使用指定的裝置上下文繪製`CCtrlView`物件的內容。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向發生繪圖的設備上下文的指標。

### <a name="remarks"></a>備註

`OnDraw`通常要求螢幕顯示,傳遞*pDC*指定的螢幕設備上下文。

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CtrlView::P重新建立視窗

在建立附加至此 `CWnd` 物件的 Windows 視窗前呼叫。

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>參數

*cs*<br/>
[創造結構](/windows/win32/api/winuser/ns-winuser-createstructw)。

### <a name="return-value"></a>傳回值

如果窗口創建應繼續,則非零;0 表示建立失敗。

### <a name="remarks"></a>備註

切勿直接調用此函數。

此函數的預設實現檢查 NULL 視窗類名稱,並替換適當的預設值。 重寫此成員函數,在`CREATESTRUCT`創建視窗之前修改結構。

派生自 的`CCtrlView`每個 類都會將自己的功能添加到`PreCreateWindow`其對 的重寫中。 根據設計,這些派生`PreCreateWindow`沒有記錄。 要確定適合每個類的樣式和樣式之間的相互依賴性,可以檢查應用程式的基類的 MFC 原始程式碼。 如果選擇重寫`PreCreateWindow`,則可以確定應用程式基類中使用的樣式是否通過使用從 MFC 原始程式碼收集的資訊提供所需的功能。

有關變更視窗樣式的詳細資訊,請參閱[變更 MFC 建立的視窗樣式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>另請參閱

[CView 類別](../../mfc/reference/cview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CTreeView 類別](../../mfc/reference/ctreeview-class.md)<br/>
[CListView 類別](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
