---
title: _ATL_FUNC_INFO 結構
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: b1c740cf1a1ed344dbceb028bd1f39a87fc09363
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168588"
---
# <a name="_atl_func_info-structure"></a>_ATL_FUNC_INFO 結構

包含用來描述分配介面上之方法或屬性的類型資訊。

## <a name="syntax"></a>語法

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>成員

`cc`<br/>
呼叫慣例。 搭配[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別使用此結構時，必須 CC_STDCALL 這個成員。 `CC_CDECL`是`CALLCONV` `_ATL_FUNC_INFO`結構的欄位 Windows CE 中唯一支援的選項。 不支援任何其他值，因此其行為未定義。

`vtReturn`<br/>
函數傳回值的 variant 類型。

`nParams`<br/>
函數參數的數目。

`pVarTypes`<br/>
函數參數之 variant 類型的陣列。

## <a name="remarks"></a>備註

就內部而言，ATL 會使用這個結構來保存從型別程式庫取得的資訊。 如果您提供搭配[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別和[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏使用之事件處理常式的類型資訊，您可能需要直接操作此結構。

## <a name="example"></a>範例

給定 IDL 中定義的分配介面方法：

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

您會定義`_ATL_FUNC_INFO`結構：

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>需求

標頭：atlcom.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
