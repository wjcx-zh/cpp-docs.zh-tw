---
title: CCRTAllocator 類
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327173"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator 類

此類提供了使用 CRT 記憶體例程式管理記憶體的方法。

## <a name="syntax"></a>語法

```
class ATL::CCRTAllocator
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCRTAllocator:分配](#allocate)|(靜態)調用此方法以分配記憶體。|
|[CCRTAllocator:免費](#free)|(靜態)調用此方法以釋放記憶體。|
|[CCRTAllocator::重新分配](#reallocate)|(靜態)調用此方法重新分配記憶體。|

## <a name="remarks"></a>備註

[CHeapPtr](../../atl/reference/cheapptr-class.md)使用此類來提供 CRT 記憶體分配例程。 對應類[CComAllocator](../../atl/reference/ccomallocator-class.md)提供了使用 COM 例程的相同方法。

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator:分配

呼叫此靜態函式以配置記憶體。

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
要配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回 void 指標至配置的空間，或如果沒有足夠的可用記憶體，則為 NULL。

### <a name="remarks"></a>備註

配置記憶體。 有關詳細資訊,請參閱[malloc。](../../c-runtime-library/reference/malloc.md)

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator:免費

調用此靜態函數以釋放記憶體。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
配置的記憶體之指標。

### <a name="remarks"></a>備註

釋放分配的記憶體。 有關詳細資訊,請參閱[免費](../../c-runtime-library/reference/free.md)。

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator::重新分配

呼叫此靜態函式以重新配置記憶體。

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
配置的記憶體之指標。

*n 位元組*<br/>
要重新配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回 void 指標至配置的空間，或如果沒有足夠的記憶體，則為 NULL。

### <a name="remarks"></a>備註

調整配置的記憶體數量。 有關詳細資訊,請參閱[realloc。](../../c-runtime-library/reference/realloc.md)

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CComallocator 類別](../../atl/reference/ccomallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
