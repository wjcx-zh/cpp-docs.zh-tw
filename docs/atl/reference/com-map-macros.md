---
title: COM 對應巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69838a690fcdddc58194caf38e3666fef023222c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028047"
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

Atl[呼叫器](../../visual-cpp-samples.md)範例：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

##  <a name="end_com_map"></a>  END_COM_MAP

結束您的 COM 介面對應的定義。

```
END_COM_MAP()
```

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[COM 對應全域函式](../../atl/reference/com-map-global-functions.md)
