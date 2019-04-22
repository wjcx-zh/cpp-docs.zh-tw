---
title: CHtmlEditView 類別
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 8267a5272d2d542c4679bf30aa9d3ad8b933d81d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767199"
---
# <a name="chtmleditview-class"></a>CHtmlEditView 類別

在 MFC 的文件/檢視架構內容中提供 WebBrowser 編輯平台的功能。

## <a name="syntax"></a>語法

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|建構 `CHtmlEditView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHtmlEditView::Create](#create)|建立新的視窗物件。|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|傳回`IHTMLDocument2`介面上目前的文件。|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|擷取此檢視的預設文件的名稱。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>需求

**Header:** afxhtml.h

##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView

建構 `CHtmlEditView` 物件。

```
CHtmlEditView();
```

##  <a name="create"></a>  CHtmlEditView::Create

建立新的視窗物件。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*lpszClassName*<br/>
指向以 null 結束的字元字串，可命名 Windows 類別。 類別名稱可以是任何名稱向[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式或`RegisterClass`Windows 函式。 如果是 NULL，會使用預先定義的預設[CFrameWnd](../../mfc/reference/cframewnd-class.md)屬性。

*lpszWindowName*<br/>
指向以 null 結束的字元字串，表示視窗名稱。

*dwStyle*<br/>
指定視窗的樣式屬性。 根據預設，會設定 WS_VISIBLE 和 WS_CHILD Windows 樣式。

*rect*<br/>
參考[RECT](/previous-versions/dd162897\(v=vs.85\))結構，指定的大小和視窗的位置。 *RectDefault*值允許指定的大小和位置的新視窗中的 Windows。

*pParentWnd*<br/>
控制項的父視窗指標。

*nID*<br/>
檢視的識別碼。 根據預設，設定為 AFX_IDW_PANE_FIRST。

*pContext*<br/>
指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)。 預設為 NULL。

### <a name="remarks"></a>備註

這個方法也會呼叫包含的 WebBrowser`Navigate`方法以載入預設文件 (請參閱 < [CHtmlEditView::GetStartDocument](#getstartdocument))。

##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument

傳回`IHTMLDocument2`介面上目前的文件。

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>參數

*ppDocument*<br/>
[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))介面。

##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument

擷取此檢視的預設文件的名稱。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>另請參閱

[HTMLEdit 範例](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
