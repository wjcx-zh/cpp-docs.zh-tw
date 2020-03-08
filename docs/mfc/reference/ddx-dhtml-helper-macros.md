---
title: DDX_DHtml Helper 宏
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866653"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml Helper 宏

DDX_DHtml helper 宏可讓您輕鬆存取 HTML 網頁上的控制項常用屬性。

### <a name="data-exchange-macros"></a>資料交換宏

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|設定或從選取的控制項抓取 Value 屬性。|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|設定或抓取目前元素的開始和結束標記之間的文字。|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|設定或抓取目前元素的開始和結束標記之間的 HTML。|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|設定或抓取目的地 URL 或錨點。|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|設定或抓取目標視窗或框架。|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|設定或抓取檔中影像或影片剪輯的名稱。|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|設定或抓取相關聯框架的 URL。|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|設定或抓取相關聯框架的 URL。|

## <a name="requirements"></a>需求

**標頭：** afxdhtml。h

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

設定或抓取目的地 URL 或錨點。

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

這個宏會使用 DISPID_IHTMLANCHORELEMENT_HREF 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

設定或抓取目標視窗或框架。

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

這個宏會使用 DISPID_IHTMLANCHORELEMENT_TARGET 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

設定或抓取目前元素的開始和結束標記之間的 HTML。

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

這個宏會使用 DISPID_IHTMLELEMENT_INNERHTML 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

設定或抓取目前元素的開始和結束標記之間的文字。

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

這個宏會使用 DISPID_IHTMLELEMENT_INNERTEXT 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

設定或從選取的控制項抓取 Value 屬性。

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。 請參閱[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)中的*值*。

## <a name="remarks"></a>備註

只有在具有 Value 屬性的控制項上執行時，這個宏才會成功。 具有 Value 屬性的控制項包括編輯方塊、清單方塊和下拉式方塊。

這個宏會使用 DISPID_A_VALUE 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

設定或抓取相關聯框架的 URL。

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

這個宏會使用 DISPID_IHTMLFRAMEBASE_SRC 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

設定或抓取相關聯框架的 URL。

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

這個宏會使用 DISPID_IHTMLFRAMEBASE_SRC 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

取得或抓取檔中影像或影片剪輯的名稱。

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*dx*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*name*<br/>
您為 HTML 控制項的 ID 參數所指定的值。

*var*<br/>
正在交換的值。

## <a name="remarks"></a>備註

使用 DDX_DHtml_Img_Src 宏來抓取 IMAGE 元素的 Src 屬性時，Internet Explorer 影像物件會傳回影像來源的完整轉義 URL。 例如，如果您使用 DDX_DHtml_Img_Src 宏，將影像元素的 Src 屬性設定為字串「一些有趣的圖片」，則 Internet Explorer 會傳回字串 "res：//d： \ myapplication \\ .exe/some %2 0 有趣的 %2 0 圖片"。

這個宏會使用 DISPID_IHTMLIMGELEMENT_SRC 分派識別碼來呼叫[CDHtmlDialog：:D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="see-also"></a>另請參閱

[CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)
