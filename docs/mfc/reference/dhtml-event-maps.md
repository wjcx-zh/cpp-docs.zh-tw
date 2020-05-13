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
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365799"
---
# <a name="dhtml-event-maps"></a>DHTML 事件對應

以下宏可用於處理 DHTML 事件。

## <a name="dhtml-event-map-macros"></a>DHTML 事件對應巨集

以下宏可用於處理[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)派生類中的 DHTML 事件。

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|標記 DHTML 事件對應。|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|標記 DHTML 事件對應。|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|聲明 DHTML 事件對應。|
|[DHTML_EVENT](#dhtml_event)|用於在單個 HTML 元素的文件等級處理事件。|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用於處理由 ActiveX 控件觸發的事件。|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用於處理具有特定 CSS 類別的所有 HTML 元素的文件等級的事件。|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用於在元素級別處理事件。|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用於從`onafterupdate`HTML 元素處理事件。|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用於從`onbeforeupdate`HTML 元素處理事件。|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用於從`onblur`HTML 元素處理事件。|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用於從`onchange`HTML 元素處理事件。|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用於從`onclick`HTML 元素處理事件。|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用於從`ondataavailable`HTML 元素處理事件。|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用於從`ondatasetchanged`HTML 元素處理事件。|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用於從`ondatasetcomplete`HTML 元素處理事件。|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用於從`ondblclick`HTML 元素處理事件。|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用於從`ondragstart`HTML 元素處理事件。|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用於從`onerrorupdate`HTML 元素處理事件。|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用於從`onfilterchange`HTML 元素處理事件。|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用於從`onfocus`HTML 元素處理事件。|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用於從`onhelp`HTML 元素處理事件。|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用於從`onkeydown`HTML 元素處理事件。|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用於從`onkeypress`HTML 元素處理事件。|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用於從`onkeyup`HTML 元素處理事件。|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用於從`onmousedown`HTML 元素處理事件。|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用於從`onmousemove`HTML 元素處理事件。|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用於從`onmouseout`HTML 元素處理事件。|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用於從`onmouseover`HTML 元素處理事件。|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用於從`onmouseup`HTML 元素處理事件。|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用於從`onresize`HTML 元素處理事件。|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用於從`onrowenter`HTML 元素處理事件。|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用於從`onrowexit`HTML 元素處理事件。|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用於從`onselectstart`HTML 元素處理事件。|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用於處理具有特定 HTML 標記的所有元素的文件等級的事件。|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|標記 DHTML 事件映射的末尾。|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|標記 DHTML 事件映射的末尾。 |

## <a name="url-event-map-macros"></a>URL 事件對應巨集

以下宏可用於處理[CMultiPageD HtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)派生類中的 DHTML 事件。

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|標記多頁 DHTML 和 URL 事件映射的開始。|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|標記嵌入 DHTML 事件映射的開始。|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|標記 URL 事件項目映射的開始。|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|聲明多頁 DHTML 和 URL 事件映射。|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|標記多頁 DHTML 和 URL 事件映射的結尾。|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|標記嵌入 DHTML 事件映射的末尾。|
|[END_URL_ENTRIES](#end_url_entries)|標記 URL 事件項目映射的末尾。|
|[URL_EVENT_ENTRY](#url_event_entry)|將 URL 或 HTML 資源映射到多頁對話框中的頁面。|

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

在源檔中放置 由`className`識別的類時,標記 DHTML 事件映射的開頭。

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 DHTML 事件映射的類的名稱。 此類應直接或間接地派生自[CDHtmlDialog,](../../mfc/reference/cdhtmldialog-class.md)並在其類定義中包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)宏。

### <a name="remarks"></a>備註

向類添加 DHTML 事件映射以`CDHtmlDialog`向其 提供資訊,這些資訊可用於將網頁中的 HTML 元素或 ActiveX 控制項觸發的事件路由到類中的處理程式函數。

將BEGIN_DHTML_EVENT_MAP宏放在類的實現 (.cpp) 檔中,然後DHTML_EVENT宏,用於該類要處理的事件(例如,DHTML_EVENT_ONMOUSEOVER滑鼠懸停事件)。 使用[END_DHTML_EVENT_MAP](#end_dhtml_event_map)宏標記事件映射的結尾。 這些巨集實現以下功能:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

在*類名稱*的類定義中標記 DHTML 事件映射的開頭。

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 DHTML 事件映射的類的名稱。 此類應直接或間接地派生自[CDHtmlDialog,](../../mfc/reference/cdhtmldialog-class.md)並在其類定義中包含[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)宏。

### <a name="remarks"></a>備註

向類添加 DHTML 事件映射以`CDHtmlDialog`向其 提供資訊,這些資訊可用於將網頁中的 HTML 元素或 ActiveX 控制項觸發的事件路由到類中的處理程式函數。

將BEGIN_DHTML_EVENT_MAP宏放在類的定義 (.h) 檔中,然後將DHTML_EVENT宏放在類要處理的事件(例如,滑鼠懸停事件DHTML_EVENT_ONMOUSEOVER)。 使用[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)宏標記事件映射的結尾。 這些巨集實現以下功能:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

在類定義中聲明 DHTML 事件映射。

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>備註

此宏將用於[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)派生類的定義。

使用[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)或[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)實現地圖。

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)宣告以下函數:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

句柄(在文件等級)由*elemName*標識的 HTML 元素識別的*未pid*事件源自。

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要處理的事件的 DISPID。

*埃萊姆納*<br/>
持有 HTML 元素的 ID 以處理文件事件的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

處理由*控制項名稱*識別的 ActiveX 控制項觸發*的不pid*觸發的事件。

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要處理的事件的調度 ID。

*控制項名稱*<br/>
持有觸發事件的控制項的 HTML ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

句柄(在文件等級)由任何 HTML 元素使用*elemName*標誌的 CSS 類發起的 *「無來源*」識別的事件。

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要處理的事件的調度 ID。

*埃萊姆納*<br/>
持有 HTML 元素的 CSS 類的 LPCWSTR,該元素來源為事件。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

句柄(在*elemName*標誌的元素)由*dispid*識別的事件。

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要處理的事件的調度 ID。

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

如果此巨集用於處理非冒泡事件,則事件源將是*elemName*識別的元素。

如果此巨集用於處理冒泡事件,*則 elemName*識別的元素可能不是事件的來源(來源可能是*elemName*包含的任何元素)。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

句柄(在文件等級),`onafterupdate`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

句柄(在文件等級),`onbeforeupdate`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

處理(在元素等級)事件`onblur`。 這是一個非冒泡事件。

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

處理(在元素等級)事件`onchange`。 這是一個非冒泡事件。

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

句柄(在文件等級),`onclick`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

句柄(在文件等級),`ondataavailable`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

句柄(在文件等級),`ondatasetchanged`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

句柄(在文件等級),`ondatasetcomplete`由`elemName`識別的 HTML 元素發起的事件。

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

句柄(在文件等級),`ondblclick`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

句柄(在文件等級),`ondragstart`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

句柄(在文件等級),`onerrorupdate`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

句柄(在文件等級),`onfilterchange`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

處理(在元素等級)事件`onfocus`。 這是一個非冒泡事件。

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

句柄(在文件等級),`onhelp`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

句柄(在文件等級),`onkeydown`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

句柄(在文件等級),`onkeypress`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

句柄(在文件等級),`onkeyup`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

句柄(在文件等級),`onmousedown`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

句柄(在文件等級),`onmousemove`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

句柄(在文件等級),`onmouseout`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

句柄(在文件等級),`onmouseover`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

句柄(在文件等級),`onmouseup`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

處理(在元素等級)事件`onresize`。 這是一個非冒泡事件。

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

句柄(在文件等級),`onrowenter`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

句柄(在文件等級),`onrowexit`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

句柄(在文件等級),`onselectstart`事件由*elemName*標誌的 HTML 元素發起。

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*埃萊姆納*<br/>
持有源事件的 HTML 元素 ID 的 LPCWSTR。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

句柄(在文件等級)由`dispid`任何 HTML 元素使用*elemName*標誌的 HTML 標記識別的事件。

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*不一部分*<br/>
要處理的事件的調度 ID。

*埃萊姆納*<br/>
原始事件的 HTML 元素的 HTML 標籤。

*成員Fxn*<br/>
事件的處理程式函數。

### <a name="remarks"></a>備註

使用此宏可向類中的[DHTML 事件映射](#begin_dhtml_event_map_inline)添加項目。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

標記 DHTML 事件映射的末尾。

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>備註

必須與[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)一起使用。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

在多頁對話框中啟動 DHTML 和 URL 事件映射的定義。

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>備註

將BEGIN_DHTML_URL_EVENT_MAP放在[CMultiPageD HtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)派生類的實現檔中。 使用[嵌入的 DHTML 事件映射](#begin_embed_dhtml_event_map)和[網址項目](#begin_url_entries)進行操作,然後用[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)將關閉。 將[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)宏包含在類定義中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

在多頁對話框中啟動嵌入 DHTML 事件映射的定義。

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含事件映射的類的名稱。 此應直接或間接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 嵌入的 DHTML 事件映射必須位於[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map)中。

*地圖名稱*<br/>
指定事件對應為其事件的頁面。 這與[URL_EVENT_ENTRY](#url_event_entry)宏中實際定義 URL 或 HTML 資源的*地圖名稱*相匹配。

### <a name="remarks"></a>備註

由於多頁 DHTML 對話方塊由多個 HTML 頁面組成,每個頁面都可以引發 DHTML 事件,因此嵌入的事件映射用於將事件映射到每個頁面的處理程式。

DHTML 和 URL 事件映射中的嵌入事件映射由BEGIN_EMBED_DHTML_EVENT_MAP宏組成,後跟[DHTML_EVENT](#dhtml_event)宏和[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)宏。

每個嵌入的事件映射都需要一個相應的[URL 事件項目](#url_event_entry),以將*mapName(BEGIN_EMBED_DHTML_EVENT_MAP*中指定)映射到 URL 或 HTML 資源。

### <a name="example"></a>範例

請參閱[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

在多頁對話方塊中啟動 URL 事件項目對應的定義。

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 URL 事件項目對應之類別的名稱。 此應直接或間接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件項目映射必須位於[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map)中。

### <a name="remarks"></a>備註

由於多頁 DHTML 對話框由多個 HTML 頁面組成,因此網址事件項目用於將網址或 HTML 資源映射到相應的[嵌入式 DHTML 事件映射](#begin_embed_dhtml_event_map)。 將URL_EVENT_ENTRY宏放在BEGIN_URL_ENTRIES和[END_URL_ENTRIES](#end_url_entries)宏之間。

### <a name="example"></a>範例

請參閱[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

在類定義中聲明 DHTML 和 URL 事件映射。

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>備註

此宏將用於[CMultiPageD HtmlDialog-](../../mfc/reference/cmultipagedhtmldialog-class.md)派生類的定義。

DHTML 和 URL 事件映射包含嵌入的[DHTML 事件映射](#begin_embed_dhtml_event_map)和[URL 事件項目](#begin_url_entries),用於按頁將 DHTML 事件映射到處理程式。 使用[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)實現映射。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

標記 DHTML 和 URL 事件映射的結尾。

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含事件映射的類的名稱。 此應直接或間接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 這應該符合[此BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)巨集中的*類別名稱*。

### <a name="example"></a>範例

請參閱[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

標記嵌入 DHTML 事件映射的末尾。

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>範例

請參閱[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

標記 URL 事件項目映射的末尾。

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>範例

請參閱[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

將 URL 或 HTML 資源映射到多頁對話框中的頁面。

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 URL 事件項目對應之類別的名稱。 此應直接或間接派生自[CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件項目映射必須位於[DHTML 和 URL 事件映射](#begin_dhtml_url_event_map)中。

*URL*<br/>
頁面的網址或 HTML 資源。

*地圖名稱*<br/>
指定其網*址為網址*的頁面。 這與[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)宏中的*地圖名稱*匹配,該宏映射此頁中的事件。

### <a name="remarks"></a>備註

如果頁面是 HTML 資源,*則 URL*必須是資源 ID 號(即"123",而不是 123 或 ID_HTMLRES1)的字串表示形式。

頁面識別符*mapName*是一個任意符號,用於將嵌入的 DHTML 事件映射連結到 URL 事件項目映射。 它在範圍上僅限於 DHTML 和 URL 事件映射。

### <a name="example"></a>範例

請參閱[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>需求

  **頭**afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

標記 DHTML 事件映射的末尾。

### <a name="syntax"></a>語法

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>備註

必須與[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)一起使用。

### <a name="requirements"></a>需求

**標題:** afxdhtml.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)
