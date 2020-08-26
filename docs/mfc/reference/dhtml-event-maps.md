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
ms.openlocfilehash: 099a08298357d99a3d09ed6fc1209d463f6a4526
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837420"
---
# <a name="dhtml-event-maps"></a>DHTML 事件對應

下列宏可以用來處理 DHTML 事件。

## <a name="dhtml-event-map-macros"></a>DHTML 事件對應宏

下列宏可以用來處理 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)衍生類別中的 DHTML 事件。

|名稱|描述|
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|標記 DHTML 事件對應的開頭。|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|標記 DHTML 事件對應的開頭。|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|宣告 DHTML 事件對應。|
|[DHTML_EVENT](#dhtml_event)|用來處理單一 HTML 元素之檔層級的事件。|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|用來處理 ActiveX 控制項所引發的事件。|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|用來處理檔層級上所有 HTML 專案具有特定 CSS 類別的事件。|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|用來處理元素層級的事件。|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|用來處理 `onafterupdate` HTML 元素的事件。|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|用來處理 `onbeforeupdate` HTML 元素的事件。|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|用來處理 `onblur` HTML 元素的事件。|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|用來處理 `onchange` HTML 元素的事件。|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|用來處理 `onclick` HTML 元素的事件。|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|用來處理 `ondataavailable` HTML 元素的事件。|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|用來處理 `ondatasetchanged` HTML 元素的事件。|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|用來處理 `ondatasetcomplete` HTML 元素的事件。|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|用來處理 `ondblclick` HTML 元素的事件。|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|用來處理 `ondragstart` HTML 元素的事件。|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|用來處理 `onerrorupdate` HTML 元素的事件。|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|用來處理 `onfilterchange` HTML 元素的事件。|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|用來處理 `onfocus` HTML 元素的事件。|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|用來處理 `onhelp` HTML 元素的事件。|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|用來處理 `onkeydown` HTML 元素的事件。|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|用來處理 `onkeypress` HTML 元素的事件。|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|用來處理 `onkeyup` HTML 元素的事件。|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|用來處理 `onmousedown` HTML 元素的事件。|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|用來處理 `onmousemove` HTML 元素的事件。|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|用來處理 `onmouseout` HTML 元素的事件。|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|用來處理 `onmouseover` HTML 元素的事件。|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|用來處理 `onmouseup` HTML 元素的事件。|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|用來處理 `onresize` HTML 元素的事件。|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|用來處理 `onrowenter` HTML 元素的事件。|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|用來處理 `onrowexit` HTML 元素的事件。|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|用來處理 `onselectstart` HTML 元素的事件。|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|用來處理檔層級的事件，以取得具有特定 HTML 標籤的所有元素。|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|標示 DHTML 事件對應的結尾。|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|標示 DHTML 事件對應的結尾。 |

## <a name="url-event-map-macros"></a>URL 事件對應宏

下列宏可以用來處理 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)衍生類別中的 DHTML 事件。

|名稱|描述|
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|標記多頁 DHTML 和 URL 事件對應的開始。|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|標記內嵌 DHTML 事件對應的開頭。|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|標記 URL 事件專案對應的開頭。|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|宣告多頁 DHTML 和 URL 事件對應。|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|標示多頁 DHTML 和 URL 事件對應的結尾。|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|標示內嵌 DHTML 事件對應的結尾。|
|[END_URL_ENTRIES](#end_url_entries)|標記 URL 事件專案對應的結尾。|
|[URL_EVENT_ENTRY](#url_event_entry)|將 URL 或 HTML 資源對應到多頁對話方塊中的頁面。|

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a> BEGIN_DHTML_EVENT_MAP

當放置在所識別之類別的原始程式檔中時，標記 DHTML 事件對應的開頭 `className` 。

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>參數

*className*<br/>
包含 DHTML 事件對應之類別的名稱。 此類別應該直接或間接衍生自 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) ，並在其類別定義中包含 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) 宏。

### <a name="remarks"></a>備註

將 DHTML 事件對應新增至您的類別，以提供資訊給 `CDHtmlDialog` ，這些資訊可以用來將網頁中的 HTML 專案或 ActiveX 控制項所引發的事件，路由至類別中的處理常式函數。

將 BEGIN_DHTML_EVENT_MAP 宏放在類別的執行 ( .cpp) 檔中，然後再針對類別要處理的事件 DHTML_EVENT 宏宏 (例如，DHTML_EVENT_ONMOUSEOVER 將滑鼠停駐事件) 。 使用 [END_DHTML_EVENT_MAP](#end_dhtml_event_map) 宏來標示事件對應的結尾。 這些宏會執行下列功能：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a> BEGIN_DHTML_EVENT_MAP_INLINE

標記類別定義中的 DHTML 事件對應的開頭（ *className*）。

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>參數

*className*<br/>
包含 DHTML 事件對應之類別的名稱。 此類別應該直接或間接衍生自 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) ，並在其類別定義中包含 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) 宏。

### <a name="remarks"></a>備註

將 DHTML 事件對應新增至您的類別，以提供資訊給 `CDHtmlDialog` ，這些資訊可以用來將網頁中的 HTML 專案或 ActiveX 控制項所引發的事件，路由至類別中的處理常式函數。

將 BEGIN_DHTML_EVENT_MAP 宏放在類別的定義中， ( .h) 檔案後面接著類別用來處理之事件的 DHTML_EVENT 宏 (例如，DHTML_EVENT_ONMOUSEOVER 隱藏的事件) 。 使用 [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) 宏來標示事件對應的結尾。 這些宏會執行下列功能：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a> DECLARE_DHTML_EVENT_MAP

在類別定義中宣告 DHTML 事件對應。

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>備註

這個宏是在 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)衍生類別的定義中使用。

使用 [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) 或 [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) 來執行對應。

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) 宣告下列函數：

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event"></a><a name="dhtml_event"></a> DHTML_EVENT

在檔層級處理 (，) *dispid* 所識別的事件源自 *elemName*所識別的 HTML 元素。

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的 DISPID。

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 專案識別碼，或為 Null 以處理檔事件。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a> DHTML_EVENT_AXCONTROL

處理由*controlnameinrow*所識別的 ActiveX 控制項所引發的*dispid*所識別的事件。

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*Controlnameinrow*<br/>
LPCWSTR，其中包含引發事件之控制項的 HTML 識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a> DHTML_EVENT_CLASS

在檔層級處理 (，) *dispid* 所識別的事件，是由 *elemName*所識別之 CSS 類別的任何 HTML 元素所產生。

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*elemName*<br/>
LPCWSTR，其中包含 HTML 專案的 CSS 類別，其為事件的來源。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a> DHTML_EVENT_ELEMENT

在 *elemName* 所識別的元素上處理 (，) 由 *dispid*識別的事件。

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

如果使用這個宏來處理 nonbubbling 事件，事件的來源將會是 *elemName*所識別的元素。

如果使用這個宏來處理反升事件， *elemName* 所識別的元素可能不是事件的來源 (來源可能是 *elemName*) 所包含的任何元素。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a> DHTML_EVENT_ONAFTERUPDATE

在檔層級處理 (，) `onafterupdate` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a> DHTML_EVENT_ONBEFOREUPDATE

在檔層級處理 (，) `onbeforeupdate` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a> DHTML_EVENT_ONBLUR

處理事件) 元素層級的 (`onblur` 。 這是 nonbubbling 事件。

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a> DHTML_EVENT_ONCHANGE

處理事件) 元素層級的 (`onchange` 。 這是 nonbubbling 事件。

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a> DHTML_EVENT_ONCLICK

在檔層級處理 (，) `onclick` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a> DHTML_EVENT_ONDATAAVAILABLE

在檔層級處理 (，) `ondataavailable` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a> DHTML_EVENT_ONDATASETCHANGED

在檔層級處理 (，) `ondatasetchanged` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a> DHTML_EVENT_ONDATASETCOMPLETE

在檔層級處理 (，) `ondatasetcomplete` 由所識別的 HTML 元素所產生的事件 `elemName` 。

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a> DHTML_EVENT_ONDBLCLICK

在檔層級處理 (，) `ondblclick` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a> DHTML_EVENT_ONDRAGSTART

在檔層級處理 (，) `ondragstart` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a> DHTML_EVENT_ONERRORUPDATE

在檔層級處理 (，) `onerrorupdate` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a> DHTML_EVENT_ONFILTERCHANGE

在檔層級處理 (，) `onfilterchange` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a> DHTML_EVENT_ONFOCUS

處理事件) 元素層級的 (`onfocus` 。 這是 nonbubbling 事件。

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a> DHTML_EVENT_ONHELP

在檔層級處理 (，) `onhelp` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a> DHTML_EVENT_ONKEYDOWN

在檔層級處理 (，) `onkeydown` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a> DHTML_EVENT_ONKEYPRESS

在檔層級處理 (，) `onkeypress` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a> DHTML_EVENT_ONKEYUP

在檔層級處理 (，) `onkeyup` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a> DHTML_EVENT_ONMOUSEDOWN

在檔層級處理 (，) `onmousedown` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a> DHTML_EVENT_ONMOUSEMOVE

在檔層級處理 (，) `onmousemove` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a> DHTML_EVENT_ONMOUSEOUT

在檔層級處理 (，) `onmouseout` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a> DHTML_EVENT_ONMOUSEOVER

在檔層級處理 (，) `onmouseover` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a> DHTML_EVENT_ONMOUSEUP

在檔層級處理 (，) `onmouseup` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a> DHTML_EVENT_ONRESIZE

處理事件) 元素層級的 (`onresize` 。 這是 nonbubbling 事件。

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a> DHTML_EVENT_ONROWENTER

在檔層級處理 (，) `onrowenter` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a> DHTML_EVENT_ONROWEXIT

在檔層級處理 (，) `onrowexit` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a> DHTML_EVENT_ONSELECTSTART

在檔層級處理 (，) `onselectstart` 由 *elemName*所識別的 HTML 元素所產生的事件。

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>參數

*elemName*<br/>
LPCWSTR，其中包含事件來源的 HTML 元素的識別碼。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a> DHTML_EVENT_TAG

在檔層級處理 (，) 由 `dispid` *elemName*所識別的 html 標記之 html 專案所識別的事件。

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>參數

*dispid*<br/>
要處理之事件的分派識別碼。

*elemName*<br/>
HTML 元素的 HTML 標籤，以事件為來源。

*memberFxn*<br/>
事件的處理常式函式。

### <a name="remarks"></a>備註

使用這個宏將專案加入至類別中的 [DHTML 事件對應](#begin_dhtml_event_map_inline) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a> END_DHTML_EVENT_MAP

標示 DHTML 事件對應的結尾。

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>備註

必須搭配 [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)使用。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a> BEGIN_DHTML_URL_EVENT_MAP

在多頁對話方塊中啟動 DHTML 和 URL 事件對應的定義。

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>備註

將 BEGIN_DHTML_URL_EVENT_MAP 放在 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)衍生類別的實檔案中。 將其與 [內嵌的 DHTML 事件對應](#begin_embed_dhtml_event_map) 和 [URL 專案](#begin_url_entries)搭配使用，然後使用 [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)將其關閉。 在類別定義中包含 [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) 宏。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a> BEGIN_EMBED_DHTML_EVENT_MAP

在多頁對話方塊中啟動內嵌 DHTML 事件對應的定義。

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>參數

*className*<br/>
包含事件對應之類別的名稱。 此類別應該直接或間接衍生自 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 內嵌 DHTML 事件對應必須在 [DHTML 和 URL 事件對應](#begin_dhtml_url_event_map)) 內。

*mapName*<br/>
指定其事件對應的頁面。 這會符合[URL_EVENT_ENTRY](#url_event_entry)宏中實際定義 URL 或 HTML 資源的*mapName* 。

### <a name="remarks"></a>備註

由於多頁 DHTML 對話方塊是由多個 HTML 網頁所組成，每一個網頁都可以引發 DHTML 事件，因此會使用內嵌的事件對應，將事件對應至每個頁面的處理常式。

DHTML 和 URL 事件對應中的內嵌事件對應是由 BEGIN_EMBED_DHTML_EVENT_MAP 巨集群組成，後面接著 [DHTML_EVENT](#dhtml_event) 宏和 [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) 宏。

每個內嵌的事件對應都需要對應的 [url 事件專案](#url_event_entry) ，才能將 BEGIN_EMBED_DHTML_EVENT_MAP) 中所指定的 *mapName* (對應至 URL 或 HTML 資源。

### <a name="example"></a>範例

請參閱 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a> BEGIN_URL_ENTRIES

在多頁對話方塊中啟動 URL 事件項目對應的定義。

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>參數

*className*<br/>
包含 URL 事件項目對應之類別的名稱。 此類別應該直接或間接衍生自 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件專案對應必須在 [DHTML 和 url 事件對應](#begin_dhtml_url_event_map)) 內。

### <a name="remarks"></a>備註

因為多頁 DHTML 對話方塊是由多個 HTML 網頁所組成，所以會使用 URL 事件專案，將 Url 或 HTML 資源對應至對應的 [內嵌 DHTML 事件](#begin_embed_dhtml_event_map)對應。 將 URL_EVENT_ENTRY 宏放在 BEGIN_URL_ENTRIES 和 [END_URL_ENTRIES](#end_url_entries) 宏之間。

### <a name="example"></a>範例

請參閱 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a> DECLARE_DHTML_URL_EVENT_MAP

在類別定義中宣告 DHTML 和 URL 事件對應。

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>備註

這個宏是在 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)衍生類別的定義中使用。

DHTML 和 URL 事件對應包含 [內嵌的 dhtml 事件對應](#begin_embed_dhtml_event_map) 和 [url 事件專案](#begin_url_entries) ，以每頁為基礎將 DHTML 事件對應至處理常式。 使用 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) 來執行對應。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a> END_DHTML_URL_EVENT_MAP

標記 DHTML 和 URL 事件對應的結尾。

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>參數

*className*<br/>
包含事件對應之類別的名稱。 此類別應該直接或間接衍生自 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 這應該符合對應[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)宏中的*className* 。

### <a name="example"></a>範例

請參閱 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a> END_EMBED_DHTML_EVENT_MAP

標示內嵌 DHTML 事件對應的結尾。

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>範例

請參閱 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="end_url_entries"></a><a name="end_url_entries"></a> END_URL_ENTRIES

標記 URL 事件專案對應的結尾。

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>範例

請參閱 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="url_event_entry"></a><a name="url_event_entry"></a> URL_EVENT_ENTRY

將 URL 或 HTML 資源對應到多頁對話方塊中的頁面。

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>參數

*className*<br/>
包含 URL 事件項目對應之類別的名稱。 此類別應該直接或間接衍生自 [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)。 URL 事件專案對應必須在 [DHTML 和 url 事件對應](#begin_dhtml_url_event_map)) 內。

*url*<br/>
頁面的 URL 或 HTML 資源。

*mapName*<br/>
指定其 URL 為 *url*的頁面。 這會比對從這個頁面對應事件的[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)宏中的*mapName* 。

### <a name="remarks"></a>備註

如果頁面是 HTML 資源，則 *url* 必須是資源識別碼的字串表示 (也就是 "123"，而不是123或 ID_HTMLRES1) 。

頁面識別碼 *mapName*是用來將內嵌的 DHTML 事件對應連結至 URL 事件專案對應的任意符號。 它受限於 DHTML 和 URL 事件對應的範圍。

### <a name="example"></a>範例

請參閱 [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)中的範例。

### <a name="requirements"></a>規格需求

  **標頭** afxdhtml。h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a> END_DHTML_EVENT_MAP_INLINE

標示 DHTML 事件對應的結尾。

### <a name="syntax"></a>語法

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>備註

必須搭配 [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)使用。

### <a name="requirements"></a>規格需求

**標頭：** afxdhtml。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)
