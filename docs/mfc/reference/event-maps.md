---
title: 事件對應
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: aa11dbe1a0a3dc45893d1a05cda0ef1addb9e665
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837342"
---
# <a name="event-maps"></a>事件對應

每當控制項要通知其容器已發生一些動作 (例如按鍵動作、滑鼠點選或變更為控制項的狀態) 時 (由控制項開發人員決定)，會呼叫引發事件函式。 這個函式會透過引發相關事件，來通知控制項容器已發生一些重要動作。

MFC 程式庫會針對引發事件提供最佳化的程式設計模型。 在這個模型中，是使用「事件對應」來指定要對特定控制項由哪些函式來引發哪些事件。 事件對應對於每個事件都會包含一個巨集。 例如，引發內建 Click 事件的事件對應可能如下所示：

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK`宏指出控制項將會在每次偵測到滑鼠點擊時引發 Stock click 事件。 如需其他內建事件的詳細清單，請參閱 [ActiveX 控制項：事件](../../mfc/mfc-activex-controls-events.md)一文。 巨集也可用於表示自訂事件。

雖然事件對應巨集很重要，但您通常不會直接將它們插入。 這是因為當您使用它來將事件引發函式與事件產生關聯時，**類別檢視**) 中的 [**屬性**] 視窗 (會自動在您的原始程式檔中建立事件對應專案。 每當您想要編輯或加入事件對應專案時，都可以使用 [ **屬性** ] 視窗。

為支援事件對應，MFC 提供下列巨集：

## <a name="event-map-macros"></a>事件對應宏

### <a name="event-map-declaration-and-demarcation"></a>事件對應宣告和區分

|名稱|描述|
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|宣告事件對應將用於類別中，以將事件對應至事件引發函式 (必須在類別宣告中使用)。|
|[BEGIN_EVENT_MAP](#begin_event_map)|開始事件對應的定義 (必須在類別實作中使用)。|
|[END_EVENT_MAP](#end_event_map)|結束事件對應的定義 (必須在類別實作中使用)。|

### <a name="event-mapping-macros"></a>事件對應巨集

|名稱|描述|
|-|-|
|[EVENT_CUSTOM](#event_custom)|指出將引發指定事件的事件引發函式。|
|[EVENT_CUSTOM_ID](#event_custom_id)|使用指定的分派 ID，指出將引發指定事件的事件引發函式。|

### <a name="message-mapping-macros"></a>訊息對應巨集

|名稱|描述|
|-|-|
|[ON_OLEVERB](#on_oleverb)|指出由 OLE 控制項處理的自訂動詞。|
|[ON_STDOLEVERB](#on_stdoleverb)|覆寫 OLE 控制項的標準動詞對應。|

## <a name="declare_event_map"></a><a name="declare_event_map"></a> DECLARE_EVENT_MAP

`COleControl`您程式中的每個衍生類別都可以提供事件對應，以指定您的控制項將引發的事件。

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>備註

在類別宣告的結尾使用 DECLARE_EVENT_MAP 宏。 然後，在定義類別成員函式的 .cpp 檔案中，使用 BEGIN_EVENT_MAP 宏、每個控制項事件的宏專案，以及用來宣告事件清單結尾的 END_EVENT_MAP 宏。

如需事件對應的詳細資訊，請參閱 [ActiveX 控制項：事件](../../mfc/mfc-activex-controls-events.md)一文。

### <a name="requirements"></a>規格需求

**標頭** afxctl.h。h

## <a name="begin_event_map"></a><a name="begin_event_map"></a> BEGIN_EVENT_MAP

開始事件對應的定義。

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定事件對應所屬的控制項類別名稱。

*baseClass*<br/>
指定 *theClass*基類的名稱。

### <a name="remarks"></a>備註

在為您的類別定義成員函式的 ( .cpp) 檔中，使用 BEGIN_EVENT_MAP 宏來啟動事件對應，然後加入每個事件的宏專案，然後使用 END_EVENT_MAP 宏來完成事件對應。

如需事件對應和 BEGIN_EVENT_MAP 宏的詳細資訊，請參閱 [ActiveX 控制項：事件](../../mfc/mfc-activex-controls-events.md)一文。

### <a name="requirements"></a>規格需求

**標頭** afxctl.h。h

## <a name="end_event_map"></a><a name="end_event_map"></a> END_EVENT_MAP

使用 END_EVENT_MAP 宏來結束事件對應的定義。

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>規格需求

**標頭** afxctl.h。h

## <a name="event_custom"></a><a name="event_custom"></a> EVENT_CUSTOM

定義自訂事件的事件對應專案。

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>參數

*pszName*<br/>
事件的名稱。

*pfnFire*<br/>
事件引發函數的名稱。

*vtsParams*<br/>
一或多個以空格分隔的清單，其中有一個或多個常數指定函式的參數清單。

### <a name="remarks"></a>備註

*VtsParams*參數是從常數以空格分隔的值清單 `VTS_` 。 其中一個或多個以空格分隔的值， (不是逗號) 指定函式的參數清單。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定清單，其中包含代表 RGB 色彩值的32位整數，後面接著指向 `IFontDisp` OLE 字型物件介面的指標。

`VTS_`常數和其意義如下：

|符號|參數類型|
|------------|--------------------|
|VTS_I2|**`short`**|
|VTS_I4|**`long`**|
|VTS_R4|**`float`**|
|VTS_R8|**`double`**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|CURRENCY|
|VTS_DATE|日期|
|VTS_BSTR|**`const`**__char \* __|
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
> 已針對所有 variant 型別定義了其他變異常數，但 VTS_FONT 和 VTS_PICTURE 例外，提供 variant 資料常數的指標。 這些常數會使用慣例來命名 `VTS_Pconstantname` 。 例如，VTS_PCOLOR 是 VTS_COLOR 常數的指標。

### <a name="requirements"></a>規格需求

**標頭** afxctl.h。h

## <a name="event_custom_id"></a><a name="event_custom_id"></a> EVENT_CUSTOM_ID

針對屬於 *dispid*所指定分派識別碼的自訂事件，定義事件引發函數。

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

*dispid*<br/>
引發事件時，控制項所使用的分派識別碼。

*pfnFire*<br/>
事件引發函數的名稱。

*vtsParams*<br/>
引發事件時，傳遞至控制項容器之參數的變數清單。

### <a name="remarks"></a>備註

*VtsParams*引數是從常數以空格分隔的值清單 `VTS_` 。 以空格分隔的一或多個值（而不是逗號）會指定函式的參數清單。 例如：

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定清單，其中包含代表 RGB 色彩值的32位整數，後面接著指向 `IFontDisp` OLE 字型物件介面的指標。

如需 `VTS_` 常數清單，請參閱 [EVENT_CUSTOM](#event_custom)。

### <a name="requirements"></a>規格需求

**標頭** afxctl.h。h

## <a name="on_oleverb"></a><a name="on_oleverb"></a> ON_OLEVERB

此宏會定義將自訂動詞對應至控制項之特定成員函式的訊息對應專案。

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>參數

*idsVerbName*<br/>
動詞名稱的字串資源識別碼。

*memberFxn*<br/>
當叫用動詞時，由框架呼叫的函式。

### <a name="remarks"></a>備註

資源編輯器可以用來建立自訂的動詞名稱，並加入至您的字串資料表。

*MemberFxn*的函式原型是：

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

*LpMsg*、 *hWndParent*和*lpRect*參數的值取自成員函式的對應參數 `IOleObject::DoVerb` 。

### <a name="requirements"></a>規格需求

**標頭** afxole。h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a> ON_STDOLEVERB

使用這個巨集覆寫標準動詞的預設行為。

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>參數

*iVerb*<br/>
被覆寫之動詞的標準動詞索引。

*memberFxn*<br/>
當叫用動詞時，由框架呼叫的函式。

### <a name="remarks"></a>備註

標準動詞索引的格式為 `OLEIVERB_` ，後面接著動作。 OLEIVERB_SHOW、OLEIVERB_HIDE 和 OLEIVERB_UIACTI加值稅E 是標準動詞的一些範例。

如需當做*memberFxn*參數使用之函式原型的描述，請參閱[ON_OLEVERB](#on_oleverb) 。

### <a name="requirements"></a>規格需求

**標頭** afxole。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
