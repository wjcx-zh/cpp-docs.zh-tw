---
title: CAtl 檔案映射類別
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318964"
---
# <a name="catlfilemapping-class"></a>CAtl 檔案映射類別

此類表示記憶體映射檔,將強制轉換運算符添加到[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>參數

*T*<br/>
用於強制轉換運算符的資料類型。

## <a name="members"></a>成員

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlFile映射::運算元 T*](#operator_t_star)|允許將`CAtlFileMapping`物件隱式轉換`T*`為 。|

## <a name="remarks"></a>備註

此新增單個強制轉換運算子,讓允許`CAtlFileMapping`將物件隱式轉換為`T*`。 其他成員由基類[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)提供。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CAtlFile 映射庫](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>需求

**標題:** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFile映射::運算元 T*

允許將`CAtlFileMapping`物件隱式轉換`T*`為 。

```
operator T*() const throw();
```

### <a name="return-value"></a>傳回值

返回指向`T*`記憶體映射檔的開頭的指標。

### <a name="remarks"></a>備註

調用[CAtlFileMappingBase:getData](../../atl/reference/catlfilemappingbase-class.md#getdata)並將返回的指標重新解釋`T*`為*T*是用作此類範本參數的類型的類型。

## <a name="see-also"></a>另請參閱

[CAtlFile對應基質](../../atl/reference/catlfilemappingbase-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
