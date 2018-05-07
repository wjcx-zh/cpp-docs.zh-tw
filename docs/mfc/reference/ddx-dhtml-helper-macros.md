---
title: DDX_DHtml Helper 巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2e9d2494463b502fda85c03fa1b861e1182cfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ddxdhtml-helper-macros"></a>DDX_DHtml Helper 巨集
DDX_DHtml helper 巨集可以讓您輕鬆存取常用的 HTML 網頁上的控制項屬性。  
  
### <a name="data-exchange-macros"></a>資料交換巨集  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|設定或擷取值屬性，從選取的控制項。|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|設定或擷取目前項目的開始和結束標記之間的文字。|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|設定或擷取目前項目的開始和結束標記之間的 HTML。|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|設定或擷取目的地 URL 或錨點。|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|設定或擷取的目標視窗或框架。|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|設定或擷取映像或文件中的視訊剪輯的名稱。|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|設定或擷取相關聯的畫面格的 URL。|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|設定或擷取相關聯的畫面格的 URL。|  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href
設定或擷取目的地 URL 或錨點。  
  
  
  
```  
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLANCHORELEMENT_HREF 分派識別碼。

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target
 設定或擷取的目標視窗或框架。  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLANCHORELEMENT_TARGET 分派識別碼。  

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml
 設定或擷取目前項目的開始和結束標記之間的 HTML。  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLELEMENT_INNERHTML 分派識別碼。  
  

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText
設定或擷取目前項目的開始和結束標記之間的文字。  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLELEMENT_INNERTEXT 分派識別碼。 

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue  
設定或擷取值屬性，從選取的控制項。  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。 請參閱*值*中[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)。  
  
## <a name="remarks"></a>備註  
 在具有 Value 屬性的控制項上執行時，此巨集才會成功。 具有 Value 屬性的控制項包含編輯方塊、 清單方塊和下拉式方塊。  
  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_A_VALUE 分派識別碼。  

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src
設定或擷取相關聯的畫面格的 URL。  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLFRAMEBASE_SRC 分派識別碼。  

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src
設定或擷取相關聯的畫面格的 URL。  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLFRAMEBASE_SRC 分派識別碼。 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
取得或擷取映像或文件中的視訊剪輯的名稱。  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>參數  
 `dx`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。  
  
 `name`  
 您指定 HTML 控制項的 ID 參數的值。  
  
 `var`  
 交換值。  
  
## <a name="remarks"></a>備註  
 當使用`DDX_DHtml_Img_Src`巨集來擷取影像項目時，Internet Explorer 映像物件的 src 屬性會傳回完全逸出的映像來源 URL。 例如，如果您使用`DDX_DHtml_Img_Src`巨集，以將影像項目 src 屬性設定為字串"一些有趣圖片，"Internet Explorer 時擷取該屬性時，會傳回字串"res://d:\myapplication\myapp.exe/some%20interesting %20picture。 」  
  
 這個巨集會呼叫[CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext)函式使用 DISPID_IHTMLIMGELEMENT_SRC 分派識別碼。  

  
## <a name="see-also"></a>另請參閱  
 [CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)
