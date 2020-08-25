---
title: COM 對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 100402e17ca1bee5f338c37f2315fbc4898a713e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833578"
---
# <a name="com-map-macros"></a>COM 對應宏

這些宏會定義 COM 介面對應。

|巨集|描述|
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面對應專案的開頭。|
|[END_COM_MAP](#end_com_map)|標記 COM 介面對應專案的結尾。|

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="begin_com_map"></a><a name="begin_com_map"></a> BEGIN_COM_MAP

COM 對應是一種機制，可透過將物件上的介面公開至用戶端 `QueryInterface` 。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在您要公開介面之類別物件的名稱。

### <a name="remarks"></a>備註

[CComObjectRootEx：： InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) 只會傳回 COM 對應中的介面指標。 使用 BEGIN_COM_MAP 宏來啟動您的介面對應、使用 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 宏或其中一個變體來新增每個介面的專案，並使用 [END_COM_MAP](#end_com_map) 宏來完成對應。

### <a name="example"></a>範例

從 ATL [BEEPER](../../overview/visual-cpp-samples.md) 範例：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a> END_COM_MAP

結束 COM 介面對應的定義。

```
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[COM 對應全域函式](../../atl/reference/com-map-global-functions.md)
