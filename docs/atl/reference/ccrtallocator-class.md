---
title: CCRTAllocator 類別
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
ms.openlocfilehash: c08d594e1c0f4d532f46961e266bf6ced98c51b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259075"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator 類別

這個類別提供方法來管理使用 CRT 記憶體常式的記憶體。

## <a name="syntax"></a>語法

```
class ATL::CCRTAllocator
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCRTAllocator::Allocate](#allocate)|（靜態）呼叫這個方法來配置記憶體。|
|[CCRTAllocator::Free](#free)|（靜態）呼叫這個方法來釋放記憶體。|
|[CCRTAllocator::Reallocate](#reallocate)|（靜態）呼叫這個方法來重新配置記憶體。|

## <a name="remarks"></a>備註

此類別由[CHeapPtr](../../atl/reference/cheapptr-class.md)提供 CRT 記憶體配置常式。 對應類別[CComAllocator](../../atl/reference/ccomallocator-class.md)，提供相同的方法使用 COM 常式。

## <a name="requirements"></a>需求

**標頭：** atlcore.h

##  <a name="allocate"></a>  CCRTAllocator::Allocate

呼叫此靜態函式以配置記憶體。

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*nBytes*<br/>
要配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回 void 指標至配置的空間，或如果沒有足夠的可用記憶體，則為 NULL。

### <a name="remarks"></a>備註

配置記憶體。 請參閱[malloc](../../c-runtime-library/reference/malloc.md)如需詳細資訊。

##  <a name="free"></a>  CCRTAllocator::Free

呼叫此靜態函式來釋放記憶體。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
配置的記憶體之指標。

### <a name="remarks"></a>備註

釋放配置的記憶體。 請參閱[免費](../../c-runtime-library/reference/free.md)如需詳細資訊。

##  <a name="reallocate"></a>  CCRTAllocator::Reallocate

呼叫此靜態函式以重新配置記憶體。

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
配置的記憶體之指標。

*nBytes*<br/>
要重新配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回 void 指標至配置的空間，或如果沒有足夠的記憶體，則為 NULL。

### <a name="remarks"></a>備註

調整配置的記憶體數量。 請參閱[realloc](../../c-runtime-library/reference/realloc.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱

[CHeapPtr 類別](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator 類別](../../atl/reference/ccomallocator-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
