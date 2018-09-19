---
title: _ATL_FUNC_INFO 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac285921500107b85c30eba4d2f1940c93721d0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113054"
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 結構

包含用來描述在分配介面上的方法或屬性的型別資訊。

## <a name="syntax"></a>語法

```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>成員

`cc`<br/>
呼叫慣例。 使用這個結構時[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別，這個成員必須是 CC_STDCALL。 `CC_CDECL` 是唯一的選項，支援 Windows CE`CALLCONV`欄位`_ATL_FUNC_INFO`結構。 任何其他值都不支援因此其行為未定義。

`vtReturn`<br/>
Variant 類型函式的傳回值。

`nParams`<br/>
函式參數數目。

`pVarTypes`<br/>
函式參數的 variant 類型的陣列。

## <a name="remarks"></a>備註

就內部而言，ATL 還會使用此結構來容納從類型程式庫取得的資訊。 如果您提供搭配使用的事件處理常式的型別資訊直接操作此結構時，您可能需要[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)類別和[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)巨集。

## <a name="example"></a>範例

指定在 IDL 中定義的 dispinterface 方法：

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

您會定義`_ATL_FUNC_INFO`結構：

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>需求

標頭： atlcom.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)

