---
title: 事件接收對應
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365727"
---
# <a name="event-sink-maps"></a>事件接收對應

當內嵌的 OLE Automation 控制項引發某個事件時，控制項的容器會使用由 MFC 提供的機制 (稱為「事件接收對應」) 來接收事件。 這個事件接收對應會指定每個特定事件的處理常式，以及那些事件函式的參數。 有關事件接收器對應的詳細資訊,請參考文章[ActiveX 控制容器](../../mfc/activex-control-containers.md)。

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

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

開始定義事件接收器映射。

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>參數

*類別*<br/>
指定其事件接收器映射為該控制項類的名稱。

*基類*<br/>
指定*類*的基類的名稱。

### <a name="remarks"></a>備註

在定義類成員函數的實現 (.cpp) 檔中,使用BEGIN_EVENTSINK_MAP宏啟動事件接收器映射,然後為要通知的每個事件添加宏條目,然後使用END_EVENTSINK_MAP宏完成事件接收器映射。

有關事件接收器映射和 OLE 控制容器的詳細資訊,請參閱文章[ActiveX 控制容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

OLE 容器可以提供事件接收器映射,以指定容器將收到通知的事件。

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>備註

在類聲明末尾使用DECLARE_EVENTSINK_MAP宏。 然後,在中。用於定義類的成員函數的 CPP 檔,使用要通知的每個事件的BEGIN_EVENTSINK_MAP宏、宏條目,以及END_EVENTSINK_MAP宏來聲明事件接收器清單的結束。

有關事件接收器對應的詳細資訊,請參考文章[ActiveX 控制容器](../../mfc/activex-control-containers.md)。

### <a name="requirements"></a>需求

  **頭**afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

結束您的事件接收器對應的定義。

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

使用ON_EVENT宏為由 OLE 控制件觸發的事件定義事件處理程式函數。

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*類別*<br/>
此事件接收器映射所屬的類。

*id*<br/>
OLE 控制項的控制識別碼。

*不一部分*<br/>
控件觸發的事件的調度 ID。

*普芬漢德勒*<br/>
指向處理事件的成員函數的指標。 此函數應具有 BOOL 返回類型和匹配事件參數的參數類型(請參閱*vtsParams)。* 該函數應返回 TRUE 以指示事件已處理;因此,應返回 TRUE,以指示事件已處理。否則 FALSE。

*vtsParams*<br/>
指定事件參數類型的**VTS_** 常量序列。 這些是調度映射條目(如DISP_FUNCTION)中使用的相同常量。

### <a name="remarks"></a>備註

*vtsParams*參數是**VTS_常量**中由空間分隔的值清單。 一個或多個這些值由空格(不是逗號)分隔,指定函數的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數後跟 BOOL 的清單。

有關**VTS_** 常量的清單,請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

使用ON_EVENT_RANGE巨集為任何 OLE 控制件觸發的事件定義事件處理程式函數,該控制項在連續 ID 範圍內具有控制項 ID。

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*類別*<br/>
此事件接收器映射所屬的類。

*idFirst*<br/>
範圍內第一個 OLE 控制項的控制 ID。

*idLast*<br/>
範圍內最後一個 OLE 控制項的控制 ID。

*不一部分*<br/>
控件觸發的事件的調度 ID。

*普芬漢德勒*<br/>
指向處理事件的成員函數的指標。 此函數應具有 BOOL 傳回類型、UINT 類型(用於控制項 ID)的第一個參數,以及與事件參數匹配的其他參數類型(請參閱*vtsParams)。* 該函數應返回 TRUE 以指示事件已處理;因此,應返回 TRUE,以指示事件已處理。否則 FALSE。

*vtsParams*<br/>
指定事件參數類型的**VTS_** 常量序列。 對於控件 ID,第一個常量應為VTS_I4類型。 這些是調度映射條目(如DISP_FUNCTION)中使用的相同常量。

### <a name="remarks"></a>備註

*vtsParams*參數是**VTS_常量**中由空間分隔的值清單。 一個或多個這些值由空格(不是逗號)分隔,指定函數的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數後跟 BOOL 的清單。

有關**VTS_** 常量的清單,請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="example"></a>範例

下面的示例演示了為三個控件(IDC_MYCTRL1 通過IDC_MYCTRL3)為滑鼠關閉事件實現的事件處理程式。 事件處理常式函`OnRangeMouseDown`數 , 在對話`CMyDlg`方塊類別 ( ) 的標頭檔中宣告為:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

下面的代碼在對話方塊類的實現檔中定義。

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

ON_EVENT_REFLECT宏在 OLE 控制件的包裝類的事件接收器映射中使用時,在控制項的容器處理事件之前接收控制項觸發的事件。

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>參數

*類別*<br/>
此事件接收器映射所屬的類。

*不一部分*<br/>
控件觸發的事件的調度 ID。

*普芬漢德勒*<br/>
指向處理事件的成員函數的指標。 此函數應具有與事件參數匹配的 BOOL 返回類型和參數類型(請參閱*vtsParams)。* 該函數應返回 TRUE 以指示事件已處理;因此,應返回 TRUE,以指示事件已處理。否則 FALSE。

*vtsParams*<br/>
指定事件參數類型的**VTS_** 常量序列。 這些是調度映射條目(如DISP_FUNCTION)中使用的相同常量。

### <a name="remarks"></a>備註

*vtsParams*參數是**VTS_常量**中由空間分隔的值清單。

一個或多個這些值由空格(不是逗號)分隔,指定函數的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數後跟 BOOL 的清單。

有關**VTS_** 常量的清單,請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

使用ON_PROPNOTIFY宏定義事件接收器映射條目,用於處理來自 OLE 控件的屬性通知。

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*類別*<br/>
此事件接收器映射所屬的類。

*id*<br/>
OLE 控制項的控制識別碼。

*不一部分*<br/>
通知中涉及的屬性的調度 ID。

*pfn 請求*<br/>
指向處理此屬性`OnRequestEdit`通知的成員函數的指標。 此功能應具有 BOOL 返回類型和**BOOL**<strong>\*</strong>參數。 此函數應將參數設置為 TRUE,以允許屬性更改,FALSE 不允許。 該函數應返回 TRUE 以指示已處理通知;否則 FALSE。

*pfn 改變*<br/>
指向處理此屬性`OnChanged`通知的成員函數的指標。 該函數應具有 BOOL 返回類型和 UINT 參數。 該函數應返回 TRUE 以指示已處理通知;否則 FALSE。

### <a name="remarks"></a>備註

*vtsParams*參數是**VTS_常量**中由空間分隔的值清單。 一個或多個這些值由空格(不是逗號)分隔,指定函數的參數清單。 例如：

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

指定包含短整數後跟 BOOL 的清單。

有關**VTS_** 常量的清單,請參閱[EVENT_CUSTOM](event-maps.md#event_custom)。

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

使用ON_PROPNOTIFY_RANGE宏定義事件接收器映射條目,用於處理來自任何 OLE 控件的屬性通知,該控制項具有連續 ID 範圍內的控制 ID。

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*類別*<br/>
此事件接收器映射所屬的類。

*idFirst*<br/>
範圍內第一個 OLE 控制項的控制 ID。

*idLast*<br/>
範圍內最後一個 OLE 控制項的控制 ID。

*不一部分*<br/>
通知中涉及的屬性的調度 ID。

*pfn 請求*<br/>
指向處理此屬性`OnRequestEdit`通知的成員函數的指標。 此函數應具有`BOOL`返回類型和`UINT`和`BOOL*`參數。 該函數應將參數設置為 TRUE,以允許屬性更改,FALSE 將不允許。 該函數應返回 TRUE 以指示已處理通知;否則 FALSE。

*pfn 改變*<br/>
指向處理此屬性`OnChanged`通知的成員函數的指標。 函數應有`BOOL`傳回型態`UINT`與參數 。 該函數應返回 TRUE 以指示已處理通知;否則 FALSE。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

ON_PROPNOTIFY_REFLECT宏在 OLE 控制件的包裝類的事件接收器對應中使用時,接收控制項在控制項的容器處理之前發送的屬性通知。

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>參數

*類別*<br/>
此事件接收器映射所屬的類。

*不一部分*<br/>
通知中涉及的屬性的調度 ID。

*pfn 請求*<br/>
指向處理此屬性`OnRequestEdit`通知的成員函數的指標。 此功能應具有 BOOL 返回類型和**BOOL**<strong>\*</strong>參數。 此函數應將參數設置為 TRUE,以允許屬性更改,FALSE 不允許。 該函數應返回 TRUE 以指示已處理通知;否則 FALSE。

*pfn 改變*<br/>
指向處理此屬性`OnChanged`通知的成員函數的指標。 該函數應具有 BOOL 返回類型,但沒有參數。 該函數應返回 TRUE 以指示已處理通知;否則 FALSE。

### <a name="requirements"></a>需求

  **標題**afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
