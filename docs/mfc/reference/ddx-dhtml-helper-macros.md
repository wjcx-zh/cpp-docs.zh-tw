---
title: DDX_DHtml 協助程式巨集
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
ms.openlocfilehash: f78a923a498713867c13ccc88e3e30c1f0a23885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365875"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml 協助程式巨集

DDX_DHtml幫助器巨集允許輕鬆存取 HTML 頁上控制項的常用屬性。

### <a name="data-exchange-macros"></a>資料交換巨集

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|從所選控制件設置或檢索 Value 屬性。|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|設置或檢索當前元素的開始和結束標記之間的文本。|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|在目前元素的開始和結束標記之間設置或檢索 HTML。|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|設置或檢索目標 URL 或錨點。|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|設置或檢索目標視窗或框架。|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|設置或檢索文件中圖像或視頻剪輯的名稱。|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|設置或檢索關聯幀的 URL。|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|設置或檢索關聯幀的 URL。|

## <a name="requirements"></a>需求

**標題:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

設置或檢索目標 URL 或錨點。

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

此巨集使用DISPID_IHTMLANCHORELEMENT_HREF調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

設置或檢索目標視窗或框架。

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

此巨集使用DISPID_IHTMLANCHORELEMENT_TARGET調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

在目前元素的開始和結束標記之間設置或檢索 HTML。

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

此巨集使用DISPID_IHTMLELEMENT_INNERHTML調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

設置或檢索當前元素的開始和結束標記之間的文本。

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

此巨集使用DISPID_IHTMLELEMENT_INNERTEXT調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

從所選控制件設置或檢索 Value 屬性。

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。 請參考*value* [CDHtmlDialog 的值::DDX_DHtml_元素文字](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)。

## <a name="remarks"></a>備註

僅當在具有 Value 屬性的控制項上運行時,此宏才會成功。 具有 Value 屬性的控制器包括編輯框、清單框和組合框。

此巨集使用DISPID_A_VALUE調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

設置或檢索關聯幀的 URL。

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

此巨集使用DISPID_IHTMLFRAMEBASE_SRC調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

設置或檢索關聯幀的 URL。

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

此巨集使用DISPID_IHTMLFRAMEBASE_SRC調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

獲取或檢索文檔中的圖像或視頻剪輯的名稱。

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>參數

*Dx*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*名稱*<br/>
為 HTML 控制項的 ID 參數指定的值。

*無 功*<br/>
要交換的值。

## <a name="remarks"></a>備註

當使用DDX_DHtml_Img_Src宏檢索 IMAGE 元素的 src 屬性時,Internet Explorer 圖像物件將返回圖像源的完全轉義 URL。 例如,如果使用DDX_DHtml_Img_Src宏將 IMAGE 元素的 src 屬性設置為字串「一些有趣的圖片」,則當您檢索該屬性時,Internet Explorer 將返回字串「res://d:_myapp.exe/某些%20有趣%20 圖片」。。

此巨集使用DISPID_IHTMLIMGELEMENT_SRC調度 ID 呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函數。

## <a name="see-also"></a>另請參閱

[CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)
