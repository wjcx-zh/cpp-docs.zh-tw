---
title: 複合控制項巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75e34fd4cfa53257f0e8a497cf8bc245c90f6732
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077346"
---
# <a name="composite-control-macros"></a>複合控制項巨集

這些巨集會定義事件接收對應 」 和 「 項目。

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|標記為複合控制項的事件接收對應的開頭。|
|[END_SINK_MAP](#end_sink_map)|將標示為複合控制項的事件接收對應的結尾。|
|[SINK_ENTRY](#sink_entry)|事件接收對應的項目。|
|[SINK_ENTRY_EX](#sink_entry_ex)|使用其他參數的事件接收對應的項目。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017)類似 SINK_ENTRY_EX，不同之處在於它接受 iid 的指標。|
|[SINK_ENTRY_INFO](#sink_entry_info)|用於以手動方式提供的型別資訊的事件接收對應的項目[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)。|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017)類似 SINK_ENTRY_INFO，不同之處在於它接受 iid 的指標。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="begin_sink_map"></a>  BEGIN_SINK_MAP

宣告為複合控制項的事件接收對應的開頭。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>參數

*（_c)*<br/>
[in]指定的控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

##  <a name="end_sink_map"></a>  END_SINK_MAP

宣告為複合控制項的事件接收對應的結尾。

```
END_SINK_MAP()
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

##  <a name="sink_entry"></a>  SINK_ENTRY

處理常式函式宣告 (*fn*) 指定的事件 (*dispid*)，所識別之控制項*識別碼*。

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>參數

*id*<br/>
[in]識別控制項。

*dispid*<br/>
[in]識別指定的事件。

*fn*<br/>
[in]事件處理常式函式的名稱。 此函式必須使用`_stdcall`呼叫慣例，而且有適當的 dispinterface 樣式的簽章。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

##  <a name="sink_entry_ex"></a>  SINK_ENTRY_EX 和 SINK_ENTRY_EX_P

處理常式函式宣告 (*fn*) 為指定的事件 (*dispid*) 的分派介面 (*iid*)，針對所識別的控制項*識別碼*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*id*<br/>
[in]識別控制項。

*iid*<br/>
[in]識別分派介面。

*piid*<br/>
[in]分派介面指標。

*dispid*<br/>
[in]識別指定的事件。

*fn*<br/>
[in]事件處理常式函式的名稱。 此函式必須使用`_stdcall`呼叫慣例，而且有適當的 dispinterface 樣式的簽章。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>備註

CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

##  <a name="sink_entry_info"></a>  SINK_ENTRY_INFO 和 SINK_ENTRY_INFO_P

使用事件接收對應內 SINK_ENTRY_INFO 巨集來提供所需的資訊[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)事件路由傳送至相關的處理常式函式。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*id*<br/>
[in]識別事件的來源不帶正負號的整數。 此值必須符合*nID*中的相關所使用的範本參數[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)基底類別。

*iid*<br/>
[in]識別分派介面的 IID。

*piid*<br/>
[in]指標，可識別分派介面的 IID。

*dispid*<br/>
[in]識別指定的事件的 DISPID。

*fn*<br/>
[in]事件處理常式函式的名稱。 此函式必須使用`_stdcall`呼叫慣例，而且有適當的 dispinterface 樣式的簽章。

*info*<br/>
[in]輸入事件處理常式函式的資訊。 此類型資訊的指標的形式提供`_ATL_FUNC_INFO`結構。 CC_CDECL 是唯一的選項，支援 Windows ce 的 CALLCONV 欄位`_ATL_FUNC_INFO`結構。 任何其他值都不支援因此其行為未定義。

### <a name="remarks"></a>備註

前四個巨集參數是相同[SINK_ENTRY_EX](#sink_entry_ex)巨集。 最後一個參數會提供事件的類型資訊。 CE ATL 實作 ActiveX 事件接收器只支援傳回值的型別 HRESULT 或 void，從您的事件處理常式方法;任何傳回的值不受支援，且其行為未定義。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[複合控制項全域函式](../../atl/reference/composite-control-global-functions.md)
