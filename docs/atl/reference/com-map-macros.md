---
title: COM 對應巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326608"
---
# <a name="com-map-macros"></a>COM 對應巨集

這些宏定義 COM 介面映射。

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面映射條目的開頭。|
|[END_COM_MAP](#end_com_map)|標記 COM 介面對應項目的末尾。|

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

COM 對應的使用者介面的連線`QueryInterface`。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]要公開介面的類物件的名稱。

### <a name="remarks"></a>備註

[CComObjectRootEx:內部查詢介面](ccomobjectrootex-class.md#internalqueryinterface)僅返回 COM 映射中介面的指標。 使用BEGIN_COM_MAP宏啟動介面映射,使用[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)宏或其變體之一為每個介面添加條目,然後使用[END_COM_MAP](#end_com_map)宏完成映射。

### <a name="example"></a>範例

從 ATL [BEEPER](../../overview/visual-cpp-samples.md)樣品中:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

結束 COM 介面映射的定義。

```
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[COM 對應全域函數](../../atl/reference/com-map-global-functions.md)
