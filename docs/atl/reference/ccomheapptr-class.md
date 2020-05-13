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
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327768"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr 類別

用於管理堆指標的智慧指標類。

## <a name="syntax"></a>語法

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在堆上的物件類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComHeapPtr:CComHeapPtr](#ccomheapptr)|建構函式。|

## <a name="remarks"></a>備註

`CComHeapPtr`派生自`CHeapPtr`,但使用[CComAllocator 器](../../atl/reference/ccomallocator-class.md)使用 COM 例程分配記憶體。 有關可用方法,請參閱[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CHeapPtrBase。](../../atl/reference/cheapptrbase-class.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr:CComHeapPtr

建構函式。

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
現有的 `CComHeapPtr` 物件。

### <a name="remarks"></a>備註

可以使用現有`CComHeapPtr`物件選擇創建堆指標。 如果是這樣,新`CComHeapPtr`對象將負責管理新的指標和資源。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)<br/>
[CComallocator 類別](../../atl/reference/ccomallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
