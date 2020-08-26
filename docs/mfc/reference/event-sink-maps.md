---
title: 事件接收對應
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 2cbfbc70ae14ccda95c377cb1587bf9d2a1ad3e6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837260"
---
# <a name="event-sink-maps"></a>事件接收對應

當內嵌的 OLE Automation 控制項引發某個事件時，控制項的容器會使用由 MFC 提供的機制 (稱為「事件接收對應」) 來接收事件。 這個事件接收對應會指定每個特定事件的處理常式，以及那些事件函式的參數。 如需事件接收對應的詳細資訊，請參閱 [ActiveX 控制項容器](../../mfc/activex-control-containers.md)文章。

### <a name="event-sink-maps"></a>事件接收對應

|名稱|描述|
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

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a> BEGIN_EVENTSINK_MAP

開始事件接收對應的定義。

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>參數

*theClass*<br/>
指定其事件接收對應的控制項類別名稱。

*baseClass*<br/>
指定 *theClass*基類的名稱。

### <a name="remarks"></a>備註

在為您的類別定義成員函式的 ( .cpp) 檔中，使用 BEGIN_EVENTSINK_MAP 宏來啟動事件接收對應，然後為每個要收到通知的事件加入宏專案，然後使用 END_EVENTSINK_MAP 宏完成事件接收對應。

如需事件接收對應和 OLE 控制項容器的詳細資訊，請參閱 [ActiveX 控制項容器](../../mfc/activex-control-containers.md)文章。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a> DECLARE_EVENTSINK_MAP

OLE 容器可以提供事件接收對應，以指定您的容器將收到通知的事件。

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>備註

在類別宣告的結尾使用 DECLARE_EVENTSINK_MAP 宏。 然後，在中。定義類別成員函式的 CPP 檔案、使用 BEGIN_EVENTSINK_MAP 宏、要通知的每個事件的宏專案，以及用來宣告事件接收器清單結尾的 END_EVENTSINK_MAP 宏。

如需事件接收對應的詳細資訊，請參閱 [ActiveX 控制項容器](../../mfc/activex-control-containers.md)文章。

### <a name="requirements"></a>規格需求

  **標頭** afxwin.h。h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a> END_EVENTSINK_MAP

結束您的事件接收器對應的定義。

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="on_event"></a><a name="on_event"></a> ON_EVENT

使用 ON_EVENT 宏來定義 OLE 控制項所引發之事件的事件處理常式函式。

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
此事件接收對應所屬的類別。

*id*<br/>
OLE 控制項的控制項 ID。

*dispid*<br/>
控制項所引發之事件的分派識別碼。

*pfnHandler*<br/>
處理事件之成員函式的指標。 此函式應該有 BOOL 傳回型別，且符合事件參數的參數類型 (參閱 *vtsParams*) 。 函數應該傳回 TRUE，表示已處理事件;否則為 FALSE。

*vtsParams*<br/>
指定事件參數類型的 **VTS_** 常數序列。 這些與分派對應專案（例如 DISP_FUNCTION）中使用的常數相同。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的**VTS_** 常數值清單。 其中一個或多個以空格分隔的值， (不是逗號) 指定函式的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數的清單，並在後面加上 BOOL。

如需 **VTS_** 常數的清單，請參閱 [EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="on_event_range"></a><a name="on_event_range"></a> ON_EVENT_RANGE

使用 ON_EVENT_RANGE 宏來定義事件處理常式函式，此函式適用于具有連續識別碼範圍內之控制項 ID 的任何 OLE 控制項所引發的事件。

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
此事件接收對應所屬的類別。

*idFirst*<br/>
範圍中第一個 OLE 控制項的控制項 ID。

*idLast*<br/>
範圍中最後一個 OLE 控制項的控制項 ID。

*dispid*<br/>
控制項所引發之事件的分派識別碼。

*pfnHandler*<br/>
處理事件之成員函式的指標。 這個函式應該有 BOOL 傳回型別、控制項 ID) 的 UINT (類型的第一個參數，以及符合事件參數的其他參數類型 (查看 *vtsParams*) 。 函數應該傳回 TRUE，表示已處理事件;否則為 FALSE。

*vtsParams*<br/>
指定事件參數類型的 **VTS_** 常數序列。 第一個常數的類型應該是 VTS_I4，以作為控制項識別碼。 這些與分派對應專案（例如 DISP_FUNCTION）中使用的常數相同。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的**VTS_** 常數值清單。 其中一個或多個以空格分隔的值， (不是逗號) 指定函式的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數的清單，並在後面加上 BOOL。

如需 **VTS_** 常數的清單，請參閱 [EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="example"></a>範例

下列範例示範事件處理常式，適用于 MouseDown 事件，可針對 ( IDC_MYCTRL1 IDC_MYCTRL3) 的三個控制項來執行。 事件處理常式函式 `OnRangeMouseDown` 是在 dialog 類別的標頭檔中宣告 ( `CMyDlg`) 為：

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

下列程式碼是在 dialog 類別的實檔案中定義。

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a> ON_EVENT_REFLECT

在 OLE 控制項的包裝函式類別的事件接收對應中使用 ON_EVENT_REFLECT 宏時，會接收控制項在由控制項的容器處理之前引發的事件。

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*theClass*<br/>
此事件接收對應所屬的類別。

*dispid*<br/>
控制項所引發之事件的分派識別碼。

*pfnHandler*<br/>
處理事件之成員函式的指標。 這個函式應該有符合事件參數的 BOOL 傳回型別和參數類型 (請參閱 *vtsParams*) 。 函數應該傳回 TRUE，表示已處理事件;否則為 FALSE。

*vtsParams*<br/>
指定事件參數類型的 **VTS_** 常數序列。 這些與分派對應專案（例如 DISP_FUNCTION）中使用的常數相同。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的**VTS_** 常數值清單。

其中一個或多個以空格分隔的值， (不是逗號) 指定函式的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數的清單，並在後面加上 BOOL。

如需 **VTS_** 常數的清單，請參閱 [EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="on_propnotify"></a><a name="on_propnotify"></a> ON_PROPNOTIFY

使用 ON_PROPNOTIFY 宏來定義事件接收對應專案，以處理來自 OLE 控制項的屬性通知。

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*theClass*<br/>
此事件接收對應所屬的類別。

*id*<br/>
OLE 控制項的控制項 ID。

*dispid*<br/>
通知中相關屬性的分派識別碼。

*pfnRequest*<br/>
成員函式的指標，該函式會處理 `OnRequestEdit` 這個屬性的通知。 這個函式應該有 BOOL 傳回型別和**bool** <strong>\*</strong> 參數。 此函式應將參數設定為 TRUE，以允許將屬性變更為 FALSE，否則不允許。 函數應該會傳回 TRUE，表示已處理通知;否則為 FALSE。

*pfnChanged*<br/>
成員函式的指標，該函式會處理 `OnChanged` 這個屬性的通知。 函數應該有 BOOL 傳回型別和 UINT 參數。 函數應該傳回 TRUE，表示已處理通知;否則為 FALSE。

### <a name="remarks"></a>備註

*VtsParams*引數是以空格分隔的**VTS_** 常數值清單。 其中一個或多個以空格分隔的值， (不是逗號) 指定函式的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數的清單，並在後面加上 BOOL。

如需 **VTS_** 常數的清單，請參閱 [EVENT_CUSTOM](event-maps.md#event_custom)。

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a> ON_PROPNOTIFY_RANGE

使用 ON_PROPNOTIFY_RANGE 宏來定義事件接收對應專案，以處理在連續識別碼範圍內具有控制項識別碼的任何 OLE 控制項的屬性通知。

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*theClass*<br/>
此事件接收對應所屬的類別。

*idFirst*<br/>
範圍中第一個 OLE 控制項的控制項 ID。

*idLast*<br/>
範圍中最後一個 OLE 控制項的控制項 ID。

*dispid*<br/>
通知中相關屬性的分派識別碼。

*pfnRequest*<br/>
成員函式的指標，該函式會處理 `OnRequestEdit` 這個屬性的通知。 此函式應該有傳回 `BOOL` 型別和 `UINT` 和 `BOOL*` 參數。 函式應將參數設定為 TRUE，以允許將屬性變更為 FALSE，否則不允許。 函數應該傳回 TRUE，表示已處理通知;否則為 FALSE。

*pfnChanged*<br/>
成員函式的指標，該函式會處理 `OnChanged` 這個屬性的通知。 函數應該有傳回 `BOOL` 型別和 `UINT` 參數。 函數應該傳回 TRUE，表示已處理通知;否則為 FALSE。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a> ON_PROPNOTIFY_REFLECT

在 OLE 控制項的包裝函式類別的事件接收對應中使用 ON_PROPNOTIFY_REFLECT 宏時，會接收控制項在由控制項的容器處理之前傳送的屬性通知。

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*theClass*<br/>
此事件接收對應所屬的類別。

*dispid*<br/>
通知中相關屬性的分派識別碼。

*pfnRequest*<br/>
成員函式的指標，該函式會處理 `OnRequestEdit` 這個屬性的通知。 這個函式應該有 BOOL 傳回型別和**bool** <strong>\*</strong> 參數。 此函式應將參數設定為 TRUE，以允許將屬性變更為 FALSE，否則不允許。 函數應該會傳回 TRUE，表示已處理通知;否則為 FALSE。

*pfnChanged*<br/>
成員函式的指標，該函式會處理 `OnChanged` 這個屬性的通知。 函數應該有 BOOL 傳回型別，而且沒有任何參數。 函數應該會傳回 TRUE，表示已處理通知;否則為 FALSE。

### <a name="requirements"></a>規格需求

  **標頭** afxdisp.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
