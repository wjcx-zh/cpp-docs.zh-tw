---
title: DHTML 事件對應
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 75ceaf3d0532a557f5227e64edece2155aacb72f
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519864"
---
# <a name="dhtml-event-maps"></a>DHTML 事件對應

下列巨集可用來處理 DHTML 事件。

## <a name="dhtml-event-map-macros"></a>DHTML 事件對應巨集

下列巨集可以用來處理 DHTML 事件[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-衍生的類別。

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|標示 DHTML 事件對應的開始。|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|標示 DHTML 事件對應的開始。|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|宣告 DHTML 事件對應。|
|[DHTML_EVENT](#dhtml_event)|用來處理單一的 HTML 元素的文件層級的事件。|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用來處理 ActiveX 控制項所引發的事件。|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用來處理所有 HTML 項目，與特定的 CSS 類別的文件層級的事件。|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用來處理項目層級的事件。|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用來處理`onafterupdate`事件從 HTML 項目。|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用來處理`onbeforeupdate`事件從 HTML 項目。|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用來處理`onblur`事件從 HTML 項目。|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用來處理`onchange`事件從 HTML 項目。|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用來處理`onclick`事件從 HTML 項目。|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用來處理`ondataavailable`事件從 HTML 項目。|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用來處理`ondatasetchanged`事件從 HTML 項目。|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用來處理`ondatasetcomplete`事件從 HTML 項目。|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用來處理`ondblclick`事件從 HTML 項目。|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用來處理`ondragstart`事件從 HTML 項目。|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用來處理`onerrorupdate`事件從 HTML 項目。|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用來處理`onfilterchange`事件從 HTML 項目。|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用來處理`onfocus`事件從 HTML 項目。|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用來處理`onhelp`事件從 HTML 項目。|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用來處理`onkeydown`事件從 HTML 項目。|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用來處理`onkeypress`事件從 HTML 項目。|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用來處理`onkeyup`事件從 HTML 項目。|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用來處理`onmousedown`事件從 HTML 項目。|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用來處理`onmousemove`事件從 HTML 項目。|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用來處理`onmouseout`事件從 HTML 項目。|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用來處理`onmouseover`事件從 HTML 項目。|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用來處理`onmouseup`事件從 HTML 項目。|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用來處理`onresize`事件從 HTML 項目。|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用來處理`onrowenter`事件從 HTML 項目。|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用來處理`onrowexit`事件從 HTML 項目。|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用來處理`onselectstart`事件從 HTML 項目。|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用來處理具有特定的 HTML 標記的所有項目的文件層級的事件。|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|標示 DHTML 事件對應的結尾。|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|標示 DHTML 事件對應的結尾。 |

## <a name="url-event-map-macros"></a>URL 事件對應巨集

下列巨集可以用來處理 DHTML 事件[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-衍生的類別。

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|標記多頁 DHTML 和 URL 事件對應的開頭。|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|標示內嵌 DHTML 事件對應的開始。|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|標示開頭的 URL 事件項目對應。|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|宣告多頁 DHTML 和 URL 事件對應。|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|標示多頁 DHTML 和 URL 事件對應的結尾。|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|標示內嵌 DHTML 事件對應的結尾。|
|[END_URL_ENTRIES](#end_url_entries)|標記的結尾 URL 事件項目對應。|
|[URL_EVENT_ENTRY](#url_event_entry)|將 URL 或 HTML 資源對應至多頁對話方塊中的頁面。|

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

將標示放在類別所識別的原始程式檔中時，才會進行 DHTML 事件對應的開頭`className`。

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 DHTML 事件對應的類別名稱。 這個類別應該直接或間接衍生自[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) ，並包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)其類別定義中的巨集。

### <a name="remarks"></a>備註

DHTML 事件對應新增至您的類別，以提供資訊給`CDHtmlDialog`，可用來將事件路由的 HTML 項目或在網頁上，您的類別中的處理常式函式的 ActiveX 控制項所引發。

類別的實作檔 (.cpp) 後面接著 DHTML_EVENT 巨集，此類別是處理的事件 (例如，為 mouseover 事件 DHTML_EVENT_ONMOUSEOVER) 括住 BEGIN_DHTML_EVENT_MAP 巨集。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)巨集來標示事件對應的結尾。 這些巨集實作下列函式：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

標示的類別定義內 DHTML 事件對應的開頭*className*。

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 DHTML 事件對應的類別名稱。 這個類別應該直接或間接衍生自[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) ，並包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)其類別定義中的巨集。

### <a name="remarks"></a>備註

DHTML 事件對應新增至您的類別，以提供資訊給`CDHtmlDialog`，可用來將事件路由的 HTML 項目或在網頁上，您的類別中的處理常式函式的 ActiveX 控制項所引發。

類別的定義 (.h) 檔後面接著 DHTML_EVENT 巨集，此類別是處理的事件 (例如，為 mouseover 事件 DHTML_EVENT_ONMOUSEOVER) 括住 BEGIN_DHTML_EVENT_MAP 巨集。 使用[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)巨集來標示事件對應的結尾。 這些巨集實作下列函式：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

宣告類別定義中的 DHTML 事件對應。

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>備註

這個巨集是用於定義[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-衍生的類別。

使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或是[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)實作對應。

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)會宣告下列函式：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

（在文件層級） 會處理所識別的事件*dispid*源自所識別的 HTML 元素*elemName*。

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的 DISPID。

*elemName*<br/>
保留來源事件，HTML 項目的 ID LPCWSTR，則為 NULL 來處理文件的事件。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

處理所識別的事件*dispid*所識別的 ActiveX 控制項所引發*controlName*。

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*controlName*<br/>
保留引發事件的控制項的 HTML ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

（在文件層級） 會處理所識別的事件*dispid*所識別的 CSS 類別與任何 HTML 項目源自*elemName*。

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*elemName*<br/>
保留來源事件中 HTML 元素的 CSS 類別 LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

處理 (在所識別的元素*elemName*) 所識別事件*dispid*。

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

如果這個巨集用來處理 nonbubbling 事件，事件來源會所識別的元素*elemName*。

如果使用這個巨集來處理事件反昇事件，所識別的元素*elemName*可能不是事件來源 (來源可以是任何所包含的項目*elemName*)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

（在文件層級） 會處理`onafterupdate`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

（在文件層級） 會處理`onbeforeupdate`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

（項目層級） 會處理`onblur`事件。 這是 nonbubbling 事件。

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

（項目層級） 會處理`onchange`事件。 這是 nonbubbling 事件。

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

（在文件層級） 會處理`onclick`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

（在文件層級） 會處理`ondataavailable`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

（在文件層級） 會處理`ondatasetchanged`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

（在文件層級） 會處理`ondatasetcomplete`HTML 項目所識別的事件來源`elemName`。

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

（在文件層級） 會處理`ondblclick`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

（在文件層級） 會處理`ondragstart`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

（在文件層級） 會處理`onerrorupdate`所識別的 HTML 項目所產生的事件*elemName*。

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

（在文件層級） 會處理`onfilterchange`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

（項目層級） 會處理`onfocus`事件。 這是 nonbubbling 事件。

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

（在文件層級） 會處理`onhelp`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

（在文件層級） 會處理`onkeydown`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

（在文件層級） 會處理`onkeypress`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

（在文件層級） 會處理`onkeyup`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

（在文件層級） 會處理`onmousedown`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

（在文件層級） 會處理`onmousemove`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

（在文件層級） 會處理`onmouseout`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

（在文件層級） 會處理`onmouseover`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

（在文件層級） 會處理`onmouseup`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

（項目層級） 會處理`onresize`事件。 這是 nonbubbling 事件。

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

（在文件層級） 會處理`onrowenter`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

（在文件層級） 會處理`onrowexit`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

（在文件層級） 會處理`onselectstart`所識別的 HTML 項目所產生的事件*elemName*。

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
保存的 HTML 項目來源的事件 ID LPCWSTR。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

（在文件層級） 會處理所識別的事件`dispid`源自任何 HTML 項目所識別的 HTML 標記*elemName*。

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*elemName*<br/>
來源事件中 HTML 元素的 HTML 標記。

*memberFxn*<br/>
事件處理常式函式。

### <a name="remarks"></a>備註

若要新增的項目，以使用這個巨集[DHTML 事件對應](#begin_dhtml_event_map_inline)在您的類別。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

標示 DHTML 事件對應的結尾。

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>備註

必須用於搭配[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

在多頁對話方塊中，會啟動 DHTML 和 URL 事件對應的定義。

```
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>備註

實作檔中放置 BEGIN_DHTML_URL_EVENT_MAP 您[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-衍生的類別。 遵循它與[內嵌 DHTML 事件對應](#begin_embed_dhtml_event_map)並[URL 項目](#begin_url_entries)，然後關閉它[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)。 包含[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)類別定義中的巨集。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

在多頁對話方塊中，會啟動內嵌 DHTML 事件對應的定義。

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含事件對應的類別名稱。 這個類別應該直接或間接衍生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 內嵌的 DHTML 事件對應都必須位於[DHTML 和 URL 事件對應](#begin_dhtml_url_event_map))。

*mapName*<br/>
指定其事件對應的頁面。 這符合*mapName*中[URL_EVENT_ENTRY](#url_event_entry)巨集的實際定義的 URL 或 HTML 資源。

### <a name="remarks"></a>備註

多頁 DHTML 對話方塊包含多個 HTML 網頁，其中每一個可以引發 DHTML 事件，因為內嵌的事件對應用來將事件對應至每個頁面為基礎的處理常式。

DHTML 和 URL 事件對應中的內嵌的事件對應組成 BEGIN_EMBED_DHTML_EVENT_MAP 巨集，後面接著[DHTML_EVENT](#dhtml_event)巨集並[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)巨集。

每個內嵌的事件對應需要相對應[URL 事件項目](#url_event_entry)對應*mapName* （指定於 BEGIN_EMBED_DHTML_EVENT_MAP） 至 URL 或 HTML 資源。

### <a name="example"></a>範例

請參閱中的範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

在多頁對話方塊中啟動 URL 事件項目對應的定義。

```
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 URL 事件項目對應之類別的名稱。 這個類別應該直接或間接衍生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件項目對應必須在內部[DHTML 和 URL 事件對應](#begin_dhtml_url_event_map))。

### <a name="remarks"></a>備註

多頁 DHTML 對話方塊包含多個 HTML 網頁，因為 URL 事件項目用來對應 Url 或 HTML 資源對應[內嵌 DHTML 事件對應](#begin_embed_dhtml_event_map)。 Put URL_EVENT_ENTRY 巨集之間 BEGIN_URL_ENTRIES 並[END_URL_ENTRIES](#end_url_entries)巨集。

### <a name="example"></a>範例

請參閱中的範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

宣告在類別定義 DHTML 和 URL 事件對應。

```
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>備註

這個巨集是用於定義[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-衍生的類別。

DHTML 和 URL 事件對應包含[內嵌 DHTML 事件對應](#begin_embed_dhtml_event_map)並[URL 事件項目](#begin_url_entries)將 DHTML 事件對應至每個頁面為基礎的處理常式。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)實作對應。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

標示 DHTML 和 URL 事件對應的結尾。

```
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含事件對應的類別名稱。 這個類別應該直接或間接衍生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 這應該符合*className*中的對應[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)巨集。

### <a name="example"></a>範例

請參閱中的範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

標示內嵌 DHTML 事件對應的結尾。

```
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>範例

請參閱中的範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

標記的結尾 URL 事件項目對應。

```
END_URL_ENTRIES()
```

### <a name="example"></a>範例

請參閱中的範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

將 URL 或 HTML 資源對應至多頁對話方塊中的頁面。

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 URL 事件項目對應之類別的名稱。 這個類別應該直接或間接衍生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件項目對應必須在內部[DHTML 和 URL 事件對應](#begin_dhtml_url_event_map))。

*Url*<br/>
頁面 URL 或 HTML 資源。

*mapName*<br/>
指定的頁面的 URL *url*。 這符合*mapName*中[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)巨集，對應從這個頁面的事件。

### <a name="remarks"></a>備註

如果頁面是 HTML 資源， *url*必須是資源的識別碼 (也就是"123"，不 123 或 ID_HTMLRES1) 的字串表示。

頁識別項*mapName*，是用來連結的任意符號內嵌 DHTML 事件對應至 URL 事件項目對應。 它會受限於 DHTML 和 URL 事件對應的範圍中。

### <a name="example"></a>範例

請參閱中的範例[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)。

### <a name="requirements"></a>需求

  **標頭**afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

標示 DHTML 事件對應的結尾。

### <a name="syntax"></a>語法

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>備註

必須用於搭配[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)。

### <a name="requirements"></a>需求

**標頭：** afxdhtml.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)
