---
title: CAutoPtrArray 類別
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 11f39eac8b8d080fd840f6454f393e33ebcb9e1c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167656"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 類別

這個類別會在建立智慧型指標的陣列時提供有用的方法。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

### <a name="parameters"></a>參數

*版*<br/>
指標類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|建構函式。|

## <a name="remarks"></a>備註

這個類別會提供一個函式，並從[CAtlArray](../../atl/reference/catlarray-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)衍生方法，協助建立可儲存智慧型指標的集合類別物件。

如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>需求

**標頭：** atlcoll。h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray

建構函式。

```cpp
CAutoPtrArray() throw();
```

### <a name="remarks"></a>備註

初始化智慧型指標陣列。

## <a name="see-also"></a>另請參閱

[CAtlArray 類別](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits 類別](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList 類別](../../atl/reference/cautoptrlist-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
