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
ms.openlocfilehash: 20d4586c1ae45e5f3f56c0adbb1ecb1757084fd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752329"
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
|[Html 編輯檢視:CHtmlEditView](#chtmleditview)|建構 `CHtmlEditView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHtmlEditView:建立](#create)|創建新視窗物件。|
|[CHtml 編輯檢視:取得 Html 文件](#getdhtmldocument)|返回`IHTMLDocument2`當前文件上的介面。|
|[CHtmlEditView:取得開始檔案](#getstartdocument)|檢索此檢視的預設文件的名稱。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

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

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>Html 編輯檢視:CHtmlEditView

建構 `CHtmlEditView` 物件。

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView:建立

創建新視窗物件。

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

*lpszClass 名稱*<br/>
指向命名 Windows 類的 null 連接字串。 類名稱可以是註冊到[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函數`RegisterClass`或 Windows 函數的任何名稱。 如果為 NULL,則使用預定義的預設[CFramewnd](../../mfc/reference/cframewnd-class.md)屬性。

*lpsz 視窗名稱*<br/>
指向表示視窗名稱的 null 連接字串。

*dwStyle*<br/>
指定視窗樣式屬性。 默認情況下,將設置WS_VISIBLE和WS_CHILD Windows 樣式。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,指定視窗的大小和位置。 *rectDefault*值允許 Windows 指定新視窗的大小和位置。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
視圖的 ID 號。 默認情況下,設置為AFX_IDW_PANE_FIRST。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)的指標。 預設情況下為 NULL。

### <a name="remarks"></a>備註

此方法還將調用包含的`Navigate`WebBrowser 方法來載入預設文件(請參閱[CHtmlEditView::getStartDocument)。](#getstartdocument)

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtml 編輯檢視:取得 Html 文件

返回`IHTMLDocument2`當前文件上的介面。

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>參數

*ppDocument*<br/>
[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))介面。

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView:取得開始檔案

檢索此檢視的預設文件的名稱。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>另請參閱

[HTML編輯範例](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
