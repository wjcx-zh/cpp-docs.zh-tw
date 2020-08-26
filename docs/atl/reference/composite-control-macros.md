---
title: 複合控制項宏
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 7ac13a11646faca53b38ec610dc0388bdd14d251
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833539"
---
# <a name="composite-control-macros"></a>複合控制項宏

這些宏會定義事件接收對應和專案。

|巨集|描述|
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|標記複合控制項的事件接收對應開頭。|
|[END_SINK_MAP](#end_sink_map)|標記複合控制項的事件接收對應結尾。|
|[SINK_ENTRY](#sink_entry)|進入事件接收器對應。|
|[SINK_ENTRY_EX](#sink_entry_ex)|具有額外參數的事件接收對應專案。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)|  (Visual Studio 2017) 類似于 SINK_ENTRY_EX，只不過它會採用 iid 的指標。|
|[SINK_ENTRY_INFO](#sink_entry_info)|以手動提供的類型資訊進入事件接收對應，以搭配 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)使用。|
|[SINK_ENTRY_INFO_P](#sink_entry_info)|  (Visual Studio 2017) 類似于 SINK_ENTRY_INFO，只不過它會採用 iid 的指標。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a> BEGIN_SINK_MAP

宣告複合控制項之事件接收對應的開頭。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>參數

*_class*<br/>
在指定控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

適用于 ActiveX 事件接收器的 CE ATL 執行只支援從事件處理常式方法傳回 HRESULT 或 void 類型的值;不支援任何其他傳回值，且其行為未定義。

## <a name="end_sink_map"></a><a name="end_sink_map"></a> END_SINK_MAP

宣告複合控制項之事件接收對應的結尾。

```
END_SINK_MAP()
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

適用于 ActiveX 事件接收器的 CE ATL 執行只支援從事件處理常式方法傳回 HRESULT 或 void 類型的值;不支援任何其他傳回值，且其行為未定義。

## <a name="sink_entry"></a><a name="sink_entry"></a> SINK_ENTRY

宣告處理常式函式， () *識別碼*所識別的控制項 (*dispid*) 之指定事件的*fn* 。

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>參數

*id*<br/>
在識別控制項。

*dispid*<br/>
在識別指定的事件。

*Fn*<br/>
在事件處理常式函數的名稱。 此函式必須使用 `_stdcall` 呼叫慣例，且具有適當的分配介面樣式簽章。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

適用于 ActiveX 事件接收器的 CE ATL 執行只支援從事件處理常式方法傳回 HRESULT 或 void 類型的值;不支援任何其他傳回值，且其行為未定義。

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a> SINK_ENTRY_EX 和 SINK_ENTRY_EX_P

宣告處理常式函式 (*fn*) 適用于分派介面 (*iid*) 的指定事件 (*dispid*) ，以供*識別碼*識別的控制項使用。

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*id*<br/>
在識別控制項。

*Iid*<br/>
在識別分派介面。

*piid*<br/>
在分派介面的指標。

*dispid*<br/>
在識別指定的事件。

*Fn*<br/>
在事件處理常式函數的名稱。 此函式必須使用 `_stdcall` 呼叫慣例，且具有適當的分配介面樣式簽章。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>備註

適用于 ActiveX 事件接收器的 CE ATL 執行只支援從事件處理常式方法傳回 HRESULT 或 void 類型的值;不支援任何其他傳回值，且其行為未定義。

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a> SINK_ENTRY_INFO 和 SINK_ENTRY_INFO_P

在事件接收對應中使用 SINK_ENTRY_INFO 宏，以提供 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 將事件路由至相關處理常式函式所需的資訊。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*id*<br/>
在識別事件來源的不帶正負號的整數。 此值必須符合相關[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)基類中使用的*nID*範本參數。

*Iid*<br/>
在識別分派介面的 IID。

*piid*<br/>
在識別分派介面之 IID 的指標。

*dispid*<br/>
在DISPID 識別指定的事件。

*Fn*<br/>
在事件處理常式函數的名稱。 此函式必須使用 `_stdcall` 呼叫慣例，且具有適當的分配介面樣式簽章。

*資訊*<br/>
在事件處理常式函數的型別資訊。 此類型資訊是以結構指標的形式提供 `_ATL_FUNC_INFO` 。 CC_CDECL 是在結構的 [CALLCONV] 欄位 Windows CE 中唯一支援的選項 `_ATL_FUNC_INFO` 。 不支援任何其他值，因此其行為未定義。

### <a name="remarks"></a>備註

前四個巨集引數與 [SINK_ENTRY_EX](#sink_entry_ex) 宏的巨集引數相同。 最後一個參數會提供事件的類型資訊。 適用于 ActiveX 事件接收器的 CE ATL 執行只支援從事件處理常式方法傳回 HRESULT 或 void 類型的值;不支援任何其他傳回值，且其行為未定義。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[複合控制項全域函式](../../atl/reference/composite-control-global-functions.md)
