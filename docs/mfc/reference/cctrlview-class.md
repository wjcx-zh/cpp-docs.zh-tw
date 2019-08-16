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
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507153"
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
|[CCtrlView::CCtrlView](#cctrlview)|建構 `CCtrlView` 物件。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|由架構呼叫, 以使用指定的裝置內容繪製。|
|[CCtrlView::PreCreateWindow](#precreatewindow)|在建立附加至此 `CCtrlView` 物件的 Windows 視窗前呼叫。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|包含 view 類別的預設樣式。|
|[CCtrlView::m_strClass](#m_strclass)|包含 view 類別的 Windows 類別名稱。|

## <a name="remarks"></a>備註

類別`CCtrlView`及其衍生的[CEditView](../../mfc/reference/ceditview-class.md)、 [CListView](../../mfc/reference/clistview-class.md)、 [CTreeView](../../mfc/reference/ctreeview-class.md)和[CRichEditView](../../mfc/reference/cricheditview-class.md), 將檔視圖架構調整為 windows 95/98 和 windows NT 版本3.51 支援的新通用控制項和更新版本。 如需檔視圖架構的詳細資訊, 請參閱[檔/視圖架構](../../mfc/document-view-architecture.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cctrlview"></a>CCtrlView:: CCtrlView

建構 `CCtrlView` 物件。

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>參數

*lpszClass*<br/>
View 類別的 Windows 類別名稱。

*dwStyle*<br/>
View 類別的樣式。

### <a name="remarks"></a>備註

當建立新的框架視窗或分割視窗時, 架構會呼叫這個函式。 覆寫[CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) , 以在附加檔之後初始化視圖。 呼叫[CWnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex)來建立 Windows 物件。

##  <a name="m_strclass"></a>CCtrlView:: m_strClass

包含 view 類別的 Windows 類別名稱。

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>CCtrlView:: m_dwDefaultStyle

包含 view 類別的預設樣式。

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>備註

建立視窗時, 會套用此樣式。

##  <a name="ondraw"></a>  CCtrlView::OnDraw

由架構呼叫, 以使用指定的裝置內容`CCtrlView`來繪製物件的內容。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
繪製發生所在之裝置內容的指標。

### <a name="remarks"></a>備註

`OnDraw`通常會針對螢幕顯示呼叫, 傳遞*pDC*所指定的螢幕裝置內容。

##  <a name="precreatewindow"></a>CCtrlView::P reCreateWindow

在建立附加至此 `CWnd` 物件的 Windows 視窗前呼叫。

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>參數

*cs*<br/>
[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)結構。

### <a name="return-value"></a>傳回值

如果應該繼續建立視窗, 則為非零值;0表示建立失敗。

### <a name="remarks"></a>備註

永遠不要直接呼叫此函式。

此函式的預設實作用會檢查 Null 視窗類別名稱, 並替代適當的預設值。 覆寫這個成員函式, `CREATESTRUCT`以在建立視窗之前修改結構。

衍生自`CCtrlView`的每個類別都會將自己的功能加入`PreCreateWindow`其覆寫。 根據設計, 這些衍生的`PreCreateWindow`並未記載。 若要判斷適用于每個類別的樣式, 以及樣式之間的相互相關性, 您可以檢查應用程式基類的 MFC 原始程式碼。 如果您選擇覆寫`PreCreateWindow`, 您可以判斷應用程式的基類中使用的樣式是否提供您所需的功能, 方法是使用從 MFC 原始程式碼收集而來的資訊。

如需變更視窗樣式的詳細資訊, 請參閱[變更 MFC 所建立之視窗的樣式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>另請參閱

[CView 類別](../../mfc/reference/cview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CTreeView 類別](../../mfc/reference/ctreeview-class.md)<br/>
[CListView 類別](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
