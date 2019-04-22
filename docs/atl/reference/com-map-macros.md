---
title: COM 對應巨集
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 3159a53b5a500aa61b85cf2bc5a97d321ed6ebb5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772367"
---
# <a name="com-map-macros"></a>COM 對應巨集

這些巨集會定義 COM 介面對應。

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|標記 COM 介面對應項目的開頭。|
|[END_COM_MAP](#end_com_map)|標記 COM 介面對應項目的結尾。|

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="begin_com_map"></a>  BEGIN_COM_MAP

COM 對應是透過用戶端物件上的介面公開 （expose） 的機制`QueryInterface`。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>參數

*x*<br/>
[in]您要公開的介面的類別物件的名稱。

### <a name="remarks"></a>備註

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) COM 對應中只會傳回介面指標。 開始 BEGIN_COM_MAP 巨集的介面對應、 將項目加入您的介面，以及每個[COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry)巨集或其中一個變數，並完成地圖[END_COM_MAP](#end_com_map)巨集。

### <a name="example"></a>範例

Atl[呼叫器](../../overview/visual-cpp-samples.md)範例：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

結束您的 COM 介面對應的定義。

```
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[COM 對應全域函式](../../atl/reference/com-map-global-functions.md)
