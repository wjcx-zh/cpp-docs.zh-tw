---
title: CComHeapPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: eaa21700f63ae07565dba4b8b3b5dabac69e0168
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553724"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr 類別

用來管理堆積指標的智慧型指標類別。

## <a name="syntax"></a>語法

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在堆積上的物件類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|建構函式。|

## <a name="remarks"></a>備註

`CComHeapPtr` 衍生自`CHeapPtr`，但會使用[CComAllocator](../../atl/reference/ccomallocator-class.md)配置使用 COM 常式的記憶體。 請參閱[CHeapPtr](../../atl/reference/cheapptr-class.md)並[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)可用的方法。

## <a name="inheritance-hierarchy"></a>繼承階層

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

建構函式。

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
現有的 `CComHeapPtr` 物件。

### <a name="remarks"></a>備註

堆積指標可以選擇性地建立使用現有`CComHeapPtr`物件。 如果是的話，新`CComHeapPtr`物件負責管理資源與新的指標。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator 類別](../../atl/reference/ccomallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
