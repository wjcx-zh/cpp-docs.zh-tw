---
title: CComAllocator 類別
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
ms.openlocfilehash: de302c7a58bf1b15e63e7cd391621ed9558e5a70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497589"
---
# <a name="ccomallocator-class"></a>CComAllocator 類別

這個類別會提供使用 COM 記憶體常式來管理記憶體的方法。

## <a name="syntax"></a>語法

```
class CComAllocator
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|呼叫此靜態方法來配置記憶體。|
|[CComAllocator::Free](#free)|呼叫此靜態方法以釋放已配置的記憶體。|
|[CComAllocator::Reallocate](#reallocate)|呼叫此靜態方法來重新配置記憶體。|

## <a name="remarks"></a>備註

[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)會使用這個類別來提供 COM 記憶體配置常式。 對應的類別[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)會使用 CRT 常式提供相同的方法。

## <a name="requirements"></a>需求

**標頭:** atlbase.h。h

##  <a name="allocate"></a>CComAllocator:: Allocate

呼叫此靜態函式以配置記憶體。

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*nBytes*<br/>
要配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回 void 指標至配置的空間，或如果沒有足夠的可用記憶體，則為 NULL。

### <a name="remarks"></a>備註

配置記憶體。 如需詳細資訊, 請參閱[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) 。

##  <a name="free"></a>CComAllocator:: Free

呼叫此靜態函式以釋放已配置的記憶體。

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
配置的記憶體之指標。

### <a name="remarks"></a>備註

釋放已配置的記憶體。 如需詳細資訊, 請參閱[CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) 。

##  <a name="reallocate"></a>CComAllocator:: 重新配置

呼叫此靜態函式以重新配置記憶體。

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
配置的記憶體之指標。

*nBytes*<br/>
要重新配置的位元組數目。

### <a name="return-value"></a>傳回值

傳回已配置空間的 void 指標, 如果記憶體不足, 則傳回 Null

### <a name="remarks"></a>備註

調整配置的記憶體數量。 如需詳細資訊, 請參閱[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) 。

## <a name="see-also"></a>另請參閱

[CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator 類別](../../atl/reference/ccrtallocator-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
