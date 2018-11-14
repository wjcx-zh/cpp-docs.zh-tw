---
title: 事件接收對應
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 3e75f1d880ce767b6fdbb61b4877f0748ba779f4
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518927"
---
# <a name="event-sink-maps"></a>事件接收對應

當內嵌的 OLE Automation 控制項引發某個事件時，控制項的容器會使用由 MFC 提供的機制 (稱為「事件接收對應」) 來接收事件。 這個事件接收對應會指定每個特定事件的處理常式，以及那些事件函式的參數。 如需有關事件接收對應的詳細資訊，請參閱文章[ActiveX 控制項容器](../../mfc/activex-control-containers.md)。

### <a name="event-sink-maps"></a>事件接收對應

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|事件接收對應定義的開頭。|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|宣告事件接收對應。|
|[END_EVENTSINK_MAP](#end_eventsink_map)|事件接收對應定義的結尾。|
|[ON_EVENT](#on_event)|定義特定事件的事件處理常式。|
|[ON_EVENT_RANGE](#on_event_range)|定義一組 OLE 控制項所引發特定事件的事件處理常式。|
|[ON_EVENT_REFLECT](#on_event_reflect)|在由控制項的容器處理之前，接收控制項引發的事件。|
|[ON_PROPNOTIFY](#on_propnotify)|定義一個處理常式來處理 OLE 控制項的屬性通知。|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|定義一個處理常式來處理來自一組 OLE 控制項的屬性通知。|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|在由控制項的容器處理前，接收控制項傳送的屬性通知。|

##  <a name="begin_eventsink_map"></a>  BEGIN_EVENTSINK_MAP

開始事件接收對應的定義。

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定的事件接收對應的控制項類別的名稱。

*baseClass*<br/>
指定的基底類別的名稱*theClass*。

### <a name="remarks"></a>備註

在定義您的類別成員函式的實作 (.cpp) 檔案，啟動事件接收對應 BEGIN_EVENTSINK_MAP 巨集，則新增巨集項目，每個事件通知，並完成事件接收對應 END_EVENTSINK_MAP 巨集。

如需有關事件接收對應和 OLE 控制項容器的詳細資訊，請參閱文章[ActiveX 控制項容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="declare_eventsink_map"></a>  DECLARE_EVENTSINK_MAP

OLE 容器可提供事件接收對應，即可指定您的容器將會收到通知的事件。

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>備註

在類別宣告結尾使用 DECLARE_EVENTSINK_MAP 巨集。 然後，在。定義類別，該成員函式的 CPP 檔案使用 BEGIN_EVENTSINK_MAP 巨集、 巨集項目，針對每個通知的事件和 END_EVENTSINK_MAP 巨集，來宣告事件接收清單的結尾。

如需有關事件接收對應的詳細資訊，請參閱文章[ActiveX 控制項容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>需求

  **標頭**afxwin.h

##  <a name="end_eventsink_map"></a>  END_EVENTSINK_MAP

結束您的事件接收器對應的定義。

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="on_event"></a>  ON_EVENT

您可以使用 ON_EVENT 巨集來定義 OLE 控制項所引發事件的事件處理常式函式。

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
這個事件接收對應所屬類別。

*id*<br/>
OLE 控制項的控制項識別碼。

*dispid*<br/>
控制項所引發事件的分派 ID。

*pfnHandler*<br/>
處理事件的成員函式的指標。 此函式應該具有 BOOL 傳回類型和參數類型符合事件的參數 (請參閱*vtsParams*)。 函式應傳回 TRUE 表示已處理事件;否則為 FALSE。

*vtsParams*<br/>
一連串**VTS_** 指定事件的參數類型的常數。 這些是分派對應項目，例如 DISP_FUNCTION 中所使用的同一個常數。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的清單中的值**VTS_** 常數。 一或多個以空格 （非逗號） 分隔這些值會指定函式的參數清單。 例如: 

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含後面接著 BOOL 的短整數的清單。

取得一份**VTS_** 常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="on_event_range"></a>  ON_EVENT_RANGE

您可以使用 ON_EVENT_RANGE 巨集來定義事件處理常式函式有連續範圍的識別碼內的控制項識別碼的任何 OLE 控制項所引發的事件。

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
這個事件接收對應所屬類別。

*idFirst*<br/>
範圍中的第一個 OLE 控制項的控制項識別碼。

*idLast*<br/>
範圍中的最後一個 OLE 控制項的控制項識別碼。

*dispid*<br/>
控制項所引發事件的分派 ID。

*pfnHandler*<br/>
處理事件的成員函式的指標。 此函式應該具有 BOOL 傳回類型、 類型單位 （適用於 「 控制項 ID) 和其他的參數類型符合事件的參數的第一個參數 (請參閱*vtsParams*)。 函式應傳回 TRUE 表示已處理事件;否則為 FALSE。

*vtsParams*<br/>
一連串**VTS_** 指定事件的參數類型的常數。 第一個常數應該是型別的 VTS_I4，控制項 id。 這些是分派對應項目，例如 DISP_FUNCTION 中所使用的同一個常數。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的清單中的值**VTS_** 常數。 一或多個以空格 （非逗號） 分隔這些值會指定函式的參數清單。 例如: 

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含後面接著 BOOL 的短整數的清單。

取得一份**VTS_** 常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="example"></a>範例

下列範例示範實作針對三個控制項的 MouseDown 事件的事件處理常式，(透過 IDC_MYCTRL3 IDC_MYCTRL1)。 事件處理常式函式`OnRangeMouseDown`，在對話方塊類別的標頭檔中宣告 ( `CMyDlg`) 為：

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

下列程式碼是在對話方塊類別的實作檔案中定義。

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="on_event_reflect"></a>  ON_EVENT_REFLECT

ON_EVENT_REFLECT 巨集時使用的事件接收對應的 OLE 控制項的包裝函式類別，接收控制項的容器處理前，控制項所引發的事件。

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
這個事件接收對應所屬類別。

*dispid*<br/>
控制項所引發事件的分派 ID。

*pfnHandler*<br/>
處理事件的成員函式的指標。 此函式應該具有 BOOL 傳回類型和參數類型符合事件的參數 (請參閱*vtsParams*)。 函式應傳回 TRUE 表示已處理事件;否則為 FALSE。

*vtsParams*<br/>
一連串**VTS_** 指定事件的參數類型的常數。 這些是分派對應項目，例如 DISP_FUNCTION 中所使用的同一個常數。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的清單中的值**VTS_** 常數。

一或多個以空格 （非逗號） 分隔這些值會指定函式的參數清單。 例如: 

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含後面接著 BOOL 的短整數的清單。

取得一份**VTS_** 常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="on_propnotify"></a>  ON_PROPNOTIFY

您可以使用 ON_PROPNOTIFY 巨集來定義的事件接收對應項目處理 OLE 控制項的屬性通知。

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*theClass*<br/>
這個事件接收對應所屬類別。

*id*<br/>
OLE 控制項的控制項識別碼。

*dispid*<br/>
在通知中所涉及之屬性的分派識別碼。

*pfnRequest*<br/>
處理的成員函式指標`OnRequestEdit`這個屬性的通知。 此函式應該有傳回型別 BOOL 和**BOOL** <strong>\*</strong>參數。 此函式應該將參數設定為 TRUE，允許變更屬性，而 FALSE 表示不允許。 函式應傳回 TRUE 表示已處理通知;否則為 FALSE。

*pfnChanged*<br/>
處理的成員函式指標`OnChanged`這個屬性的通知。 函式應該有傳回型別和 UINT 參數 BOOL。 函式應傳回 TRUE，表示已處理通知;否則為 FALSE。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的清單中的值**VTS_** 常數。 一或多個以空格 （非逗號） 分隔這些值會指定函式的參數清單。 例如: 

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含後面接著 BOOL 的短整數的清單。

取得一份**VTS_** 常數，請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

##  <a name="on_propnotify_range"></a>  ON_PROPNOTIFY_RANGE

您可以使用 ON_PROPNOTIFY_RANGE 巨集來定義事件接收對應項目來處理從任何有連續範圍的識別碼內的控制項 ID 的 OLE 控制項的屬性通知。

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*theClass*<br/>
這個事件接收對應所屬類別。

*idFirst*<br/>
範圍中的第一個 OLE 控制項的控制項識別碼。

*idLast*<br/>
範圍中的最後一個 OLE 控制項的控制項識別碼。

*dispid*<br/>
在通知中所涉及之屬性的分派識別碼。

*pfnRequest*<br/>
處理的成員函式指標`OnRequestEdit`這個屬性的通知。 此函式應該具有`BOOL`傳回型別和`UINT`和`BOOL*`參數。 此函式應該將參數設定為 TRUE，允許變更屬性，而 FALSE 表示不允許。 函式應傳回 TRUE，表示已處理通知;否則為 FALSE。

*pfnChanged*<br/>
處理的成員函式指標`OnChanged`這個屬性的通知。 函式應該有`BOOL`傳回型別和`UINT`參數。 函式應傳回 TRUE，表示已處理通知;否則為 FALSE。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

##  <a name="on_propnotify_reflect"></a>  ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT 巨集時使用的事件接收對應的 OLE 控制項的包裝函式類別，會接收由控制項的容器處理之前，由控制項傳送的屬性通知。

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*theClass*<br/>
這個事件接收對應所屬類別。

*dispid*<br/>
在通知中所涉及之屬性的分派識別碼。

*pfnRequest*<br/>
處理的成員函式指標`OnRequestEdit`這個屬性的通知。 此函式應該有傳回型別 BOOL 和**BOOL** <strong>\*</strong>參數。 此函式應該將參數設定為 TRUE，允許變更屬性，而 FALSE 表示不允許。 函式應傳回 TRUE 表示已處理通知;否則為 FALSE。

*pfnChanged*<br/>
處理的成員函式指標`OnChanged`這個屬性的通知。 函式應該具有 BOOL 傳回類型和任何參數。 函式應傳回 TRUE 表示已處理通知;否則為 FALSE。

### <a name="requirements"></a>需求

  **標頭**afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
