---
title: "DHTML 事件對應 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.macros.shared
dev_langs:
- C++
helpviewer_keywords:
- event map macros
- DHTML, event map macros
- macros, DHTML event map
- DHTML events, event map
- DHTML events
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 8be59b52e06241651a2f605ab949efffd0e010d3
ms.lasthandoff: 02/24/2017

---
# <a name="dhtml-event-maps"></a>DHTML 事件對應
下列巨集可以用來處理 DHTML 事件。  
  
## <a name="dhtml-event-map-macros"></a>DHTML 事件對應巨集  
 下列巨集可以用來處理 DHTML 事件中的[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-衍生的類別。  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|標記 DHTML 事件對應的開頭。|  
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|標記 DHTML 事件對應的開頭。|  
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|宣告 DHTML 事件對應。|  
|[DHTML_EVENT](#dhtml_event)|用來處理單一的 HTML 元素的文件層級的事件。|  
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用來處理 ActiveX 控制項所引發的事件。|  
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用來處理所有 HTML 項目與特定的 CSS 類別的文件層級的事件。|  
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用來處理項目層級的事件。|  
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用來處理**onafterupdate**事件從 HTML 項目。|  
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用來處理**onbeforeupdate**事件從 HTML 項目。|  
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用來處理**onblur**事件從 HTML 項目。|  
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用來處理`onchange`事件從 HTML 項目。|  
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用來處理**onclick**事件從 HTML 項目。|  
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用來處理**ondataavailable**事件從 HTML 項目。|  
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用來處理**ondatasetchanged**事件從 HTML 項目。|  
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用來處理**ondatasetcomplete**事件從 HTML 項目。|  
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用來處理**類似**事件從 HTML 項目。|  
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用來處理**ondragstart**事件從 HTML 項目。|  
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用來處理**onerrorupdate**事件從 HTML 項目。|  
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用來處理**onfilterchange**事件從 HTML 項目。|  
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用來處理**onfocus**事件從 HTML 項目。|  
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用來處理`onhelp`事件從 HTML 項目。|  
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用來處理**onkeydown**事件從 HTML 項目。|  
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用來處理**onkeypress**事件從 HTML 項目。|  
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用來處理**onkeyup**事件從 HTML 項目。|  
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用來處理**onmousedown**事件從 HTML 項目。|  
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用來處理`onmousemove`事件從 HTML 項目。|  
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用來處理**onmouseout**事件從 HTML 項目。|  
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用來處理**onmouseover**事件從 HTML 項目。|  
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用來處理**onmouseup**事件從 HTML 項目。|  
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用來處理**onresize**事件從 HTML 項目。|  
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用來處理**onrowenter**事件從 HTML 項目。|  
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用來處理**onrowexit**事件從 HTML 項目。|  
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用來處理**onselectstart**事件從 HTML 項目。|  
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用來處理所有的項目具有特定的 HTML 標記的文件層級的事件。|  
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|DHTML 事件對應結束標記。|  
  
## <a name="url-event-map-macros"></a>URL 事件對應巨集  
 下列巨集可以用來處理 DHTML 事件中的[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-衍生的類別。  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|標記多頁 DHTML 和 URL 事件對應的開頭。|  
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|標記內嵌 DHTML 事件對應的開頭。|  
|[BEGIN_URL_ENTRIES](#begin_url_entries)|標記 URL 事件項目對應的開頭。|  
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|宣告多頁 DHTML 和 URL 事件對應。|  
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|多頁 DHTML 和 URL 事件對應結束標記。|  
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|標示內嵌 DHTML 事件對應的結束。|  
|[END_URL_ENTRIES](#end_url_entries)|URL 事件項目對應結束標記。|  
|[URL_EVENT_ENTRY](#url_event_entry)|將 URL 或 HTML 資源對應至多頁對話方塊中的頁面。|  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namebegindhtmleventmapa--begindhtmleventmap"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP  
 標記放在原始程式檔所識別的類別中時，才會進行 DHTML 事件對應的開頭`className`。  
  
```   
BEGIN_DHTML_EVENT_MAP(className)   
```  
  
### <a name="parameters"></a>參數  
 `className`  
 包含 DHTML 事件對應的類別名稱。 這個類別應直接或間接衍生從[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) ，並包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)其類別定義中的巨集。  
  
### <a name="remarks"></a>備註  
 DHTML 事件對應加入至您的類別來提供資訊給**CDHtmlDialog** ，可以用於 HTML 項目或網頁，在您的類別處理常式函式中的 ActiveX 控制項所引發的路由事件。  
  
 位置`BEGIN_DHTML_EVENT_MAP`類別的實作 (.cpp) 檔案中的巨集後面`DHTML_EVENT`巨集的事件類別是處理 (例如， `DHTML_EVENT_ONMOUSEOVER` mouseover 事件)。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)巨集，以標記事件對應的結尾。 這些巨集實作下列函式︰  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namebegindhtmleventmapinlinea--begindhtmleventmapinline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE  
 標記 DHTML 事件對應中的類別定義的開頭`className`。  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>參數  
 `className`  
 包含 DHTML 事件對應的類別名稱。 這個類別應直接或間接衍生從[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) ，並包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)其類別定義中的巨集。  
  
### <a name="remarks"></a>備註  
 DHTML 事件對應加入至您的類別來提供資訊給**CDHtmlDialog** ，可以用於 HTML 項目或網頁，在您的類別處理常式函式中的 ActiveX 控制項所引發的路由事件。  
  
 位置`BEGIN_DHTML_EVENT_MAP`類別的定義 (.h) 檔中的巨集後面`DHTML_EVENT`巨集的事件類別是處理 (例如， `DHTML_EVENT_ONMOUSEOVER` mouseover 事件)。 使用[END_DHTML_EVENT_MAP_INLINE](http://msdn.microsoft.com/library/0cfec092-20ee-49f3-bc38-56d6a5572db2)巨集，以標記事件對應的結尾。 這些巨集實作下列函式︰  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  

  
##  <a name="a-namedeclaredhtmleventmapa--declaredhtmleventmap"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP  
 宣告的類別定義 DHTML 事件對應。  
  
```   
DECLARE_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>備註  
 這個巨集是用於定義中的[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-衍生的類別。  
  
 使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)來實作對應。  
  
 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)下列函式宣告︰  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventa--dhtmlevent"></a><a name="dhtml_event"></a>DHTML_EVENT  
 處理 （在文件層級） 所識別的事件`dispid`所識別的 HTML 項目所產生`elemName`。  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 處理事件的 DISPID。  
  
 `elemName`  
 `LPCWSTR`保留來源事件，HTML 項目的 ID 或**NULL**來處理文件的事件。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventaxcontrola--dhtmleventaxcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL  
 處理所識別的事件`dispid`所識別的 ActiveX 控制項引發`controlName`。  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要處理事件的分派 ID。  
  
 `controlName`  
 `LPCWSTR`保留 HTML 控制項的 ID 而引發事件。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventclassa--dhtmleventclass"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS  
 處理 （在文件層級） 所識別的事件`dispid`所識別的 CSS 類別的任何 HTML 項目是源自`elemName`。  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要處理事件的分派 ID。  
  
 `elemName`  
 `LPCWSTR`保留來源事件中 HTML 元素的 CSS 類別。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventelementa--dhtmleventelement"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT  
 處理 (所識別的項目`elemName`) 所識別的事件`dispid`。  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要處理事件的分派 ID。  
  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
 如果這個巨集用來處理 nonbubbling 事件，事件來源會所識別的元素`elemName`。  
  
 如果這個巨集用來處理反昇事件，所識別之項目的`elemName`可能不是事件來源 (來源可能是由包含任何項目`elemName`)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonafterupdatea--dhtmleventonafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE  
 （在文件層級） 處理**onafterupdate**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonbeforeupdatea--dhtmleventonbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE  
 （在文件層級） 處理**onbeforeupdate**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonblura--dhtmleventonblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR  
 （在項目層級） 處理**onblur**事件。 這是 nonbubbling 事件。  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonchangea--dhtmleventonchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE  
 （在項目層級） 處理`onchange`事件。 這是 nonbubbling 事件。  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonclicka--dhtmleventonclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK  
 （在文件層級） 處理**onclick**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventondataavailablea--dhtmleventondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE  
 （在文件層級） 處理**ondataavailable**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventondatasetchangeda--dhtmleventondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED  
 （在文件層級） 處理**ondatasetchanged**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventondatasetcompletea--dhtmleventondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE  
 （在文件層級） 處理**ondatasetcomplete**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventondblclicka--dhtmleventondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK  
 （在文件層級） 處理**類似**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventondragstarta--dhtmleventondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART  
 （在文件層級） 處理**ondragstart**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonerrorupdatea--dhtmleventonerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE  
 （在文件層級） 處理**onerrorupdate**所識別的 HTML 項目所產生的事件`elemName`。  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonfilterchangea--dhtmleventonfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE  
 （在文件層級） 處理**onfilterchange**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonfocusa--dhtmleventonfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS  
 （在項目層級） 處理**onfocus**事件。 這是 nonbubbling 事件。  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonhelpa--dhtmleventonhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP  
 （在文件層級） 處理`onhelp`所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeydowna--dhtmleventonkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN  
 （在文件層級） 處理**onkeydown**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeypressa--dhtmleventonkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS  
 （在文件層級） 處理**onkeypress**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonkeyupa--dhtmleventonkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP  
 （在文件層級） 處理**onkeyup**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmousedowna--dhtmleventonmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN  
 （在文件層級） 處理**onmousedown**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmousemovea--dhtmleventonmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE  
 （在文件層級） 處理`onmousemove`所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseouta--dhtmleventonmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT  
 （在文件層級） 處理**onmouseout**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseovera--dhtmleventonmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER  
 （在文件層級） 處理**onmouseover**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonmouseupa--dhtmleventonmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP  
 （在文件層級） 處理**onmouseup**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonresizea--dhtmleventonresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE  
 （在項目層級） 處理**onresize**事件。 這是 nonbubbling 事件。  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonrowentera--dhtmleventonrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER  
 （在文件層級） 處理**onrowenter**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonrowexita--dhtmleventonrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT  
 （在文件層級） 處理**onrowexit**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventonselectstarta--dhtmleventonselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART  
 （在文件層級） 處理**onselectstart**所識別的 HTML 項目所產生的事件`elemName`。  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>參數  
 `elemName`  
 `LPCWSTR`保留來源事件之 HTML 項目識別碼。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedhtmleventtaga--dhtmleventtag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG  
 處理 （在文件層級） 所識別的事件`dispid`所識別的 HTML 標記的任何 HTML 項目是源自`elemName`。  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 要處理事件的分派 ID。  
  
 `elemName`  
 取得事件的 HTML 項目的 HTML 標記。  
  
 `memberFxn`  
 事件處理常式函式。  
  
### <a name="remarks"></a>備註  
 若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-nameenddhtmleventmapa--enddhtmleventmap"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP  
 DHTML 事件對應結束標記。  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>備註  
 必須搭配使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namebegindhtmlurleventmapa--begindhtmlurleventmap"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP  
 多頁對話方塊中，啟動 DHTML 和 URL 事件對應的定義。  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>備註  
 將`BEGIN_DHTML_URL_EVENT_MAP`的實作檔中您[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-衍生的類別。 請遵循與[內嵌 DHTML 事件對應](#begin_embed_dhtml_event_map)和[URL 項目](#begin_url_entries)，然後關閉它與[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)。 包含[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)在類別定義中的巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&196;](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namebeginembeddhtmleventmapa--beginembeddhtmleventmap"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP  
 多頁對話方塊中啟動內嵌 DHTML 事件對應的定義。  
  
```  
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)  
 
```  
  
### <a name="parameters"></a>參數  
 `className`  
 包含事件對應的類別名稱。 這個類別應直接或間接衍生從[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 內嵌的 DHTML 事件對應都必須位於[DHTML 和 URL 事件對應](#begin_dhtml_url_event_map))。  
  
 *mapName*  
 指定的事件對應的頁面。 這會比對*mapName*中[URL_EVENT_ENTRY](#url_event_entry)巨集實際定義的 URL 或 HTML 資源。  
  
### <a name="remarks"></a>備註  
 由於多頁 DHTML 對話方塊包含多個 HTML 網頁，其中每個可能引發 DHTML 事件，請內嵌的事件對應用來將事件對應至每個頁面為基礎的處理常式。  
  
 DHTML 和 URL 事件對應內的內嵌的事件對應組成`BEGIN_EMBED_DHTML_EVENT_MAP`後面接著巨集[DHTML_EVENT](dhtml-event-maps.md#dhtml_event)巨集和[END_EMBED_DHTML_EVENT_MAP](dhtml-event-maps.md#end_embed_dhtml_event_map)巨集。  
  
 每個內嵌的事件對應需要對應[URL 事件項目](#url_event_entry)對應*mapName* (指定在`BEGIN_EMBED_DHTML_EVENT_MAP`) 至 URL 或 HTML 資源。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namebeginurlentriesa--beginurlentries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES  
 在多頁對話方塊中啟動 URL 事件項目對應的定義。  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>參數  
 `className`  
 包含 URL 事件項目對應之類別的名稱。 這個類別應直接或間接衍生從[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件項目對應必須位於[DHTML 和 URL 事件對應](#begin_dhtml_url_event_map))。  
  
### <a name="remarks"></a>備註  
 由於多頁 DHTML 對話方塊包含多個 HTML 網頁，URL 事件項目用來對應 Url 或 HTML 資源對應至相對應[內嵌 DHTML 事件對應](#begin_embed_dhtml_event_map)。 將`URL_EVENT_ENTRY`巨集之間`BEGIN_URL_ENTRIES`和[END_URL_ENTRIES](#end_url_entries)巨集。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-namedeclaredhtmlurleventmapa--declaredhtmlurleventmap"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP  
 宣告的 DHTML 和 URL 事件對應的類別定義。  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>備註  
 這個巨集是用於定義中的[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-衍生的類別。  
  
 DHTML 和 URL 事件對應包含[內嵌 DHTML 事件對應](#begin_embed_dhtml_event_map)和[URL 事件項目](#begin_url_entries)DHTML 事件對應至每個頁面為基礎的處理常式。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)來實作對應。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-nameenddhtmlurleventmapa--enddhtmlurleventmap"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP  
 標示 DHTML 和 URL 事件對應的結束。  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>參數  
 `className`  
 包含事件對應的類別名稱。 這個類別應直接或間接衍生從[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 這應該要符合`className`在對應[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)巨集。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-nameendembeddhtmleventmapa--endembeddhtmleventmap"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP  
 標示內嵌 DHTML 事件對應的結束。  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-nameendurlentriesa--endurlentries"></a><a name="end_url_entries"></a>END_URL_ENTRIES  
 URL 事件項目對應結束標記。  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
  
##  <a name="a-nameurlevententrya--urlevententry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY  
 將 URL 或 HTML 資源對應至多頁對話方塊中的頁面。  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>參數  
 `className`  
 包含 URL 事件項目對應之類別的名稱。 這個類別應直接或間接衍生從[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件項目對應必須位於[DHTML 和 URL 事件對應](#begin_dhtml_url_event_map))。  
  
 *url*  
 網頁 URL 或 HTML 資源。  
  
 *mapName*  
 指定的頁面的 URL 是*url*。 這會比對*mapName*中[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)巨集，對應從這個頁面的事件。  
  
### <a name="remarks"></a>備註  
 如果頁面是 HTML 資源， *url*必須是資源識別碼 (也就是"123"，不 123 或 ID_HTMLRES1) 的字串表示。  
  
 頁面識別碼*mapName*，是用來連結的任意符號內嵌 DHTML 事件對應至 URL 事件項目對應。 它會在 DHTML 和 URL 事件對應的範圍受到限制。  
  
### <a name="example"></a>範例  
 請參閱範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。  

  
### <a name="requirements"></a>需求  
  **標頭**afxdhtml.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

