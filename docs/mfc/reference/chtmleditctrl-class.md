---
title: CHtmlEditCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366847"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl 類別

在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。

## <a name="syntax"></a>語法

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|建構 `CHtmlEditCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHtml 編輯Ctrl:建立](#create)|創建 Web 瀏覽器 ActiveX 控制件`CHtmlEditCtrl`並將其附加到 物件。 此功能會自動將 Web 瀏覽器 ActiveX 控制項置於編輯模式。|
|[CHtml編輯Ctrl:取得DHtml文件](#getdhtmldocument)|檢索目前在包含的 Web 瀏覽器控制項中載入的文檔上的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))介面。|
|[CHtmlEditCtrl::取得開始檔案](#getstartdocument)|檢索預設文件的網址 以載入到包含的 Web 瀏覽器控制項中。|

## <a name="remarks"></a>備註

託管 Web 瀏覽器控制程式在建立後會自動進入編輯模式。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>需求

**Header:** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl

建構 `CHtmlEditCtrl` 物件。

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtml 編輯Ctrl:建立

創建 Web 瀏覽器 ActiveX 控制件`CHtmlEditCtrl`並將其附加到 物件。 WebBrowser ActiveX 控制件會自動導航到預設文件,然後由此功能置於編輯模式。

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>參數

*lpsz 視窗名稱*<br/>
不使用這個參數。

*dwStyle*<br/>
不使用這個參數。

*矩形*<br/>
指定控制項的大小和位置。

*pparentwnd*<br/>
指定控制項的父視窗。 它不得為 NULL。

*nID*<br/>
指定控制項的識別碼。

*pContext*<br/>
不使用這個參數。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtml編輯Ctrl:取得DHtml文件

檢索目前在包含的 Web 瀏覽器控制項中載入的文件上的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))介面

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>參數

*ppDocument*<br/>
文檔介面。

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::取得開始檔案

檢索預設文件的網址 以載入到包含的 Web 瀏覽器控制項中。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)
