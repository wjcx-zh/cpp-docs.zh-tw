---
title: 事件對應
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: c79d2fb1ac73947ddb13adcbd444ff7b5d50bdb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365742"
---
# <a name="event-maps"></a>事件對應

每當控制項要通知其容器已發生一些動作 (例如按鍵動作、滑鼠點選或變更為控制項的狀態) 時 (由控制項開發人員決定)，會呼叫引發事件函式。 這個函式會透過引發相關事件，來通知控制項容器已發生一些重要動作。

MFC 程式庫會針對引發事件提供最佳化的程式設計模型。 在這個模型中，是使用「事件對應」來指定要對特定控制項由哪些函式來引發哪些事件。 事件對應對於每個事件都會包含一個巨集。 例如，引發內建 Click 事件的事件對應可能如下所示：

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

宏`EVENT_STOCK_CLICK`指示控件每次檢測到滑鼠按一下時都會觸發庫存單擊事件。 有關其他股票事件的更詳細清單,請參閱[文章 ActiveX 控制件:事件](../../mfc/mfc-activex-controls-events.md)。 巨集也可用於表示自訂事件。

雖然事件對應巨集很重要，但您通常不會直接將它們插入。 這是因為**屬性**視窗(**在類檢視中**)在使用該視窗將事件觸發函數與事件關聯時,會自動在源檔中創建事件映射條目。 任何時候要編輯或添加事件映射條目時,都可以使用 **「屬性」** 視窗。

為支援事件對應，MFC 提供下列巨集：

## <a name="event-map-macros"></a>事件對應巨集

### <a name="event-map-declaration-and-demarcation"></a>事件對應宣告和區分

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|宣告事件對應將用於類別中，以將事件對應至事件引發函式 (必須在類別宣告中使用)。|
|[BEGIN_EVENT_MAP](#begin_event_map)|開始事件對應的定義 (必須在類別實作中使用)。|
|[END_EVENT_MAP](#end_event_map)|結束事件對應的定義 (必須在類別實作中使用)。|

### <a name="event-mapping-macros"></a>事件對應巨集

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|指出將引發指定事件的事件引發函式。|
|[EVENT_CUSTOM_ID](#event_custom_id)|使用指定的分派 ID，指出將引發指定事件的事件引發函式。|

### <a name="message-mapping-macros"></a>訊息對應巨集

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|指出由 OLE 控制項處理的自訂動詞。|
|[ON_STDOLEVERB](#on_stdoleverb)|覆寫 OLE 控制項的標準動詞對應。|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

程式中`COleControl`的每個派生類都可以提供事件映射來指定控制項將觸發的事件。

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>備註

在類聲明末尾使用DECLARE_EVENT_MAP宏。 然後,在定義類成員函數的 .cpp 檔中,使用BEGIN_EVENT_MAP個宏、每個控件事件的宏條目和END_EVENT_MAP宏來聲明事件清單的結束。

有關事件映射的詳細資訊,請參閱[「ActiveX 控件:事件](../../mfc/mfc-activex-controls-events.md)」一文。

### <a name="requirements"></a>需求

**頭**afxctl.h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

開始定義事件映射。

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
指定事件對應為其事件對應的控制項類別的名稱。

*基類*<br/>
指定*類*的基類的名稱。

### <a name="remarks"></a>備註

在定義類成員函數的實現 (.cpp) 檔中,使用BEGIN_EVENT_MAP宏啟動事件映射,然後為每個事件添加宏條目,然後使用END_EVENT_MAP宏完成事件映射。

有關事件對應和BEGIN_EVENT_MAP宏的詳細資訊,請參閱[文章 ActiveX 控制項:事件](../../mfc/mfc-activex-controls-events.md)。

### <a name="requirements"></a>需求

**頭**afxctl.h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

使用END_EVENT_MAP宏結束事件映射的定義。

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>需求

**頭**afxctl.h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

為自定義事件定義事件映射條目。

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>參數

*pszName*<br/>
事件的名稱。

*普芬火*<br/>
事件觸發函數的名稱。

*vtsParams*<br/>
指定函數參數清單的一個或多個常量的空間分隔清單。

### <a name="remarks"></a>備註

*vtsParams*參數是一個空間分隔的值清單`VTS_`, 與常量。 一個或多個這些值由空格(不是逗號)分隔,指定函數的參數清單。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定包含表示 RGB 顏色值的 32 位元整數的清單,`IFontDisp`後跟指向 OLE 字型物件介面的指標。

常`VTS_`量及其含義如下:

|符號|參數類型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**長**|
|VTS_R4|**浮動**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|CURRENCY|
|VTS_DATE|日期|
|VTS_BSTR|**康斯特**__字\*元__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|HANDLE|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> 已為所有變數類型定義了其他變體常量,但提供指向變體數據常量的VTS_FONT和VTS_PICTURE除外。 這些常量使用約定`VTS_Pconstantname`命名。 例如,VTS_PCOLOR是指向VTS_COLOR常量的指標。

### <a name="requirements"></a>需求

**頭**afxctl.h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

為屬於*dispid*指定的調度 ID 的自定義事件定義事件觸發函數。

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>參數

*pszName*<br/>
事件的名稱。

*不一部分*<br/>
控件在觸發事件時使用的調度 ID。

*普芬火*<br/>
事件觸發函數的名稱。

*vtsParams*<br/>
觸發事件時傳遞給控制容器的參數的可變清單。

### <a name="remarks"></a>備註

*vtsParams*參數是空格分隔的值清單`VTS_`和 常量。 由空格(而不是逗號)分隔的一個或多個值指定函數的參數清單。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定包含表示 RGB 顏色值的 32 位元整數的清單,`IFontDisp`後跟指向 OLE 字型物件介面的指標。

有關常數的清單,`VTS_`請參考[EVENT_CUSTOM](#event_custom)。

### <a name="requirements"></a>需求

**頭**afxctl.h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

此宏定義一個消息映射條目,該條目將自定義謂詞映射到控制項的特定成員函數。

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>參數

*idsVerbName*<br/>
謂詞名稱的字串資源 ID。

*成員Fxn*<br/>
當叫用動詞時，由框架呼叫的函式。

### <a name="remarks"></a>備註

資源編輯器可用於創建添加到字串表的自定義謂詞名稱。

*成員Fxn*的功能原型是:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

lpMsg、hWndParent*hWndParent*和*lpRect*參數的`IOleObject::DoVerb`值取自 成員函數*lpMsg*的相應參數。

### <a name="requirements"></a>需求

**頭**afxole.h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

使用這個巨集覆寫標準動詞的預設行為。

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>參數

*iVerb*<br/>
被覆寫之動詞的標準動詞索引。

*成員Fxn*<br/>
當叫用動詞時，由框架呼叫的函式。

### <a name="remarks"></a>備註

標準動詞索引是形式`OLEIVERB_`,後跟一個動作。 OLEIVERB_SHOW、OLEIVERB_HIDE和OLEIVERB_UIACTIVATE是標準動詞的一些示例。

有關用作*成員Fxn*參數的功能原型的說明,請參閱[ON_OLEVERB。](#on_oleverb)

### <a name="requirements"></a>需求

**頭**afxole.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
