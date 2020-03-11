---
title: COM 對應宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864927"
---
# <a name="com-map-macros"></a>COM 對應宏

這些宏會定義 COM 介面對應。

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面對應專案的開頭。|
|[END_COM_MAP](#end_com_map)|標示 COM 介面對應專案的結尾。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="begin_com_map"></a>BEGIN_COM_MAP

COM 對應是透過 `QueryInterface`將物件上的介面公開至用戶端的機制。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>參數

*x*<br/>
在您要在其中公開介面之類別物件的名稱。

### <a name="remarks"></a>備註

[CComObjectRootEx：： InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)只會傳回 COM 對應中介面的指標。 使用 BEGIN_COM_MAP 宏來啟動您的介面對應、使用[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)宏或它的其中一個變數來新增每個介面的專案，並使用[END_COM_MAP](#end_com_map)宏完成對應。

### <a name="example"></a>範例

從 ATL [BEEPER](../../overview/visual-cpp-samples.md)範例：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>END_COM_MAP

結束 COM 介面對應的定義。

```
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[COM 對應全域函式](../../atl/reference/com-map-global-functions.md)
