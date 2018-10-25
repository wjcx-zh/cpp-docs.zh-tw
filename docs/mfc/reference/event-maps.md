---
title: 事件對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45a5b1714721a414f1016d977cc9cb549b4000d7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083109"
---
# <a name="event-maps"></a>事件對應

每當控制項要通知其容器已發生一些動作 (例如按鍵動作、滑鼠點選或變更為控制項的狀態) 時 (由控制項開發人員決定)，會呼叫引發事件函式。 這個函式會透過引發相關事件，來通知控制項容器已發生一些重要動作。

MFC 程式庫會針對引發事件提供最佳化的程式設計模型。 在這個模型中，是使用「事件對應」來指定要對特定控制項由哪些函式來引發哪些事件。 事件對應對於每個事件都會包含一個巨集。 例如，引發內建 Click 事件的事件對應可能如下所示：

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK`巨集表示控制項就會引發內建 Click 事件，每次偵測到滑鼠按一下。 如需其他內建事件更詳細的清單，請參閱文章[ActiveX 控制項： 事件](../../mfc/mfc-activex-controls-events.md)。 巨集也可用於表示自訂事件。

雖然事件對應巨集很重要，但您通常不會直接將它們插入。 這是因為當您使用它來關聯事件引發函式與事件時，[屬性] 視窗會自動在您的原始程式檔中建立事件對應項目。 每當您要編輯或加入事件對應項目時，都可以使用 [屬性] 視窗。

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

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

每個`COleControl`-在您的程式中的衍生的類別可提供事件對應至指定的控制項就會引發的事件。

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>備註

在類別宣告結尾使用 DECLARE_EVENT_MAP 巨集。 接著，在定義類別的成員函式的.cpp 檔案，使用 BEGIN_EVENT_MAP 巨集、 巨集項目為每個控制項的事件和 END_EVENT_MAP 巨集來宣告事件清單的結尾。

如需有關事件對應的詳細資訊，請參閱文章[ActiveX 控制項： 事件](../../mfc/mfc-activex-controls-events.md)。

### <a name="requirements"></a>需求

**標頭**afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

開始事件對應的定義。

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定其事件對應的控制項類別的名稱。

*baseClass*<br/>
指定的基底類別的名稱*theClass*。

### <a name="remarks"></a>備註

在定義您的類別成員函式的實作 (.cpp) 檔案，啟動事件對應 BEGIN_EVENT_MAP 巨集，然後新增巨集項目，每個事件，並完成事件對應 END_EVENT_MAP 巨集。

如需有關事件對應和 BEGIN_EVENT_MAP 巨集的詳細資訊，請參閱文章[ActiveX 控制項： 事件](../../mfc/mfc-activex-controls-events.md)。

### <a name="requirements"></a>需求

**標頭**afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

您可以使用 END_EVENT_MAP 巨集結束事件對應的定義。

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>需求

**標頭**afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM

定義自訂事件的事件對應項目。

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>參數

*pszName*<br/>
事件的名稱。

*pfnFire*<br/>
事件引發函式的名稱。

*vtsParams*<br/>
指定函式的參數清單的一或多個常數以空格分隔清單。

### <a name="remarks"></a>備註

*VtsParams*參數是以空格分隔的清單中的值`VTS_`常數。 一或多個以空格 （非逗號） 分隔這些值會指定函式的參數清單。 例如: 

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定清單，其中包含 32 位元的整數，表示 RGB 色彩值，後面接著一個指向`IFontDisp`OLE 字型物件介面。

`VTS_`常數和其意義如下：

|符號|參數類型|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|貨幣|
|VTS_DATE|DATE|
|VTS_BSTR|**const** __char\*__|
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
> 對於所有 variant 類型，除了 VTS_FONT 和 VTS_PICTURE，提供變異資料常數的指標，定義其他變數的常數。 這些常數會使用名為`VTS_Pconstantname`慣例。 比方說，VTS_PCOLOR 是 VTS_COLOR 常數的指標。

### <a name="requirements"></a>需求

**標頭**afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

定義事件引發自訂事件屬於所指定的分派識別碼的函式*dispid*。

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
事件引發函式的名稱。

*vtsParams*<br/>
引發事件時，參數的變數清單會傳遞至控制項容器。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的清單中的值`VTS_`常數。 一或多個以空格分隔，不是逗號，這些值會指定函式的參數清單。 例如: 

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

指定清單，其中包含 32 位元的整數，表示 RGB 色彩值，後面接著一個指向`IFontDisp`OLE 字型物件介面。

取得一份`VTS_`常數，請參閱[EVENT_CUSTOM](#event_custom)。

### <a name="requirements"></a>需求

**標頭**afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

這個巨集會定義訊息的對應項目對應至您的控制項的特定成員函式的自訂動詞命令。

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>參數

*idsVerbName*<br/>
動詞命令的名稱的字串資源識別碼。

*memberFxn*<br/>
當叫用動詞時，由框架呼叫的函式。

### <a name="remarks"></a>備註

資源編輯器可用來建立自訂的動詞名稱新增至字串資料表。

函式原型*memberFxn*是：

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

值*lpMsg*， *hWndParent*，並*lpRect*參數都會取自的對應參數`IOleObject::DoVerb`成員函式。

### <a name="requirements"></a>需求

**標頭**afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

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

格式是標準動詞索引`OLEIVERB_`，後面接著動作。 OLEIVERB_SHOW、 OLEIVERB_HIDE 和 OLEIVERB_UIACTIVATE 是標準動詞的一些範例。

請參閱[ON_OLEVERB](#on_oleverb)用作函式原型的說明*memberFxn*參數。

### <a name="requirements"></a>需求

**標頭**afxole.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
