---
title: 複合控制巨集
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331522"
---
# <a name="composite-control-macros"></a>複合控制巨集

這些宏定義事件接收器映射和條目。

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|標記複合控件的事件接收器映射的開頭。|
|[END_SINK_MAP](#end_sink_map)|標記複合控制件的事件接收器映射的末尾。|
|[SINK_ENTRY](#sink_entry)|進入事件接收器映射。|
|[SINK_ENTRY_EX](#sink_entry_ex)|使用附加參數進入事件接收器對應。|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (視覺工作室 2017)類似於SINK_ENTRY_EX,只不過它需要指向 iid 的指標。|
|[SINK_ENTRY_INFO](#sink_entry_info)|項目事件接收器映射與手動提供的類型資訊,用於與[IDispEventSimple.](../../atl/reference/idispeventsimpleimpl-class.md)|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (視覺工作室 2017)類似於SINK_ENTRY_INFO,只不過它需要指向 iid 的指標。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

聲明複合控件的事件接收器映射的開頭。

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>參數

*_class*<br/>
[在]指定控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

聲明複合控制項的事件接收器對應的結束。

```
END_SINK_MAP()
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

聲明*識別*碼的控制項指定事件 (*不pid)* 的處理程式函數 *(fn)。*

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>參數

*id*<br/>
[在]標識控件。

*不一部分*<br/>
[在]標識指定的事件。

*Fn*<br/>
[在]事件處理程式函數的名稱。 此函數必須使用`_stdcall`調用約定,並具有適當的非介面樣式簽名。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>備註

ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX和SINK_ENTRY_EX_P

宣告調度介面 *(iid)* 的指定事件 (*不 pid)* 的處理程式函數 *(fn),* 用於*由 id*識別的控制項。

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*id*<br/>
[在]標識控件。

*Iid*<br/>
[在]標識調度介面。

*皮伊德*<br/>
[在]指向調度介面的指標。

*不一部分*<br/>
[在]標識指定的事件。

*Fn*<br/>
[在]事件處理程式函數的名稱。 此函數必須使用`_stdcall`調用約定,並具有適當的非介面樣式簽名。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>備註

ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO和SINK_ENTRY_INFO_P

使用事件接收器映射中的SINK_ENTRY_INFO宏來提供[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)所需的資訊,以將事件路由到相關的處理程式函數。

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>參數

*id*<br/>
[在]標識事件源的無符號整數。 此值必須與相關[IDispEventSimple](../../atl/reference/idispeventsimpleimpl-class.md)基礎類中使用的*nID*範本參數匹配。

*Iid*<br/>
[在]標識調度介面的 IID。

*皮伊德*<br/>
[在]指向標識派單介面的 IID 的指標。

*不一部分*<br/>
[在]識別指定事件的 DISPID。

*Fn*<br/>
[在]事件處理程式函數的名稱。 此函數必須使用`_stdcall`調用約定,並具有適當的非介面樣式簽名。

*info*<br/>
[在]鍵入事件處理程式函數的資訊。 此類型資訊以指向`_ATL_FUNC_INFO`結構的指標的形式提供。 CC_CDECL是`_ATL_FUNC_INFO`Windows CE 中支援結構 CALLCONV 欄位的唯一選項。 任何其他值不受支援,因此其行為未定義。

### <a name="remarks"></a>備註

前四個宏參數與[SINK_ENTRY_EX](#sink_entry_ex)宏的參數相同。 最終參數提供事件的類型資訊。 ActiveX 事件接收器的 CE ATL 實現僅支援事件處理程式方法中 HRESULT 類型的傳回值或 void;任何其他返回值不受支援,其行為未定義。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[複合控制全域函數](../../atl/reference/composite-control-global-functions.md)
