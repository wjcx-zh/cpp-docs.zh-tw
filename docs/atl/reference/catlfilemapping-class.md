---
title: CAtlFileMapping 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168120"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 類別

此類別代表記憶體對應檔，並將 cast 運算子加入至[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)的方法。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>參數

*T*<br/>
用於 cast 運算子的資料類型。

## <a name="members"></a>成員

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlFileMapping：： operator T *](#operator_t_star)|允許將`CAtlFileMapping`物件隱含轉換成`T*`。|

## <a name="remarks"></a>備註

這個類別會加入單一轉換運算子，以允許將`CAtlFileMapping`物件隱含轉換`T*`成。 其他成員是由基類[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)所提供。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>需求

**標頭：** atlfile。h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping：： operator T *

允許將`CAtlFileMapping`物件隱含轉換成`T*`。

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>傳回值

傳回記憶體`T*`對應檔開頭的指標。

### <a name="remarks"></a>備註

呼叫[CAtlFileMappingBase：：](../../atl/reference/catlfilemappingbase-class.md#getdata)參數，並向量傳回的指標作為`T*` ，其中*T*是用來做為這個類別之樣板參數的類型。

## <a name="see-also"></a>另請參閱

[CAtlFileMappingBase 類別](../../atl/reference/catlfilemappingbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
