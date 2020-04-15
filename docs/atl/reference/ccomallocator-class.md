---
title: CComallocator 類別
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321145"
---
# <a name="ccomallocator-class"></a>CComallocator 類別

此類提供了使用 COM 記憶體例程管理記憶體的方法。

## <a name="syntax"></a>語法

```
class CComAllocator
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComallocator:分配](#allocate)|調用此靜態方法以分配記憶體。|
|[CComallocator:免費](#free)|調用此靜態方法以釋放分配的記憶體。|
|[CComallocator::重新分配](#reallocate)|調用此靜態方法重新分配記憶體。|

## <a name="remarks"></a>備註

[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)使用此類來提供 COM 記憶體分配例程。 對應類[CCRT 分配器](../../atl/reference/ccrtallocator-class.md)使用 CRT 例程提供相同的方法。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComallocator:分配

呼叫此靜態函式以配置記憶體。

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
要配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回 void 指標至配置的空間，或如果沒有足夠的可用記憶體，則為 NULL。

### <a name="remarks"></a>備註

配置記憶體。 有關詳細資訊[,請參閱 CoTaskMemAlloc。](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)

## <a name="ccomallocatorfree"></a><a name="free"></a>CComallocator:免費

調用此靜態函數以釋放分配的記憶體。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
配置的記憶體之指標。

### <a name="remarks"></a>備註

釋放分配的記憶體。 有關詳細資訊,請參閱[CoTaskMem 免費](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)。

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComallocator::重新分配

呼叫此靜態函式以重新配置記憶體。

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
配置的記憶體之指標。

*n 位元組*<br/>
要重新配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回指向已分配空間的空指標,如果記憶體不足,則傳回 NULL

### <a name="remarks"></a>備註

調整配置的記憶體數量。 有關詳細資訊[,請參閱 CoTaskMemRealloc。](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

## <a name="see-also"></a>另請參閱

[CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator 類](../../atl/reference/ccrtallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
