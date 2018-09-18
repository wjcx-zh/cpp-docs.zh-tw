---
title: CComHeap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b38aabbb418a355f85917a2d287c2f473cb2e7df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062913"
---
# <a name="ccomheap-class"></a>CComHeap 類別

這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 COM 記憶體配置函式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComHeap::Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[Ccomheap:: Free](#free)|呼叫這個方法來釋放此記憶體管理員所配置的記憶體區塊。|
|[CComHeap::GetSize](#getsize)|呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。|
|[Ccomheap:: Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CComHeap` 實作使用 COM 配置功能，包括記憶體配置函式[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)， [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree)， [IMalloc::GetSize](/windows/desktop/api/objidlbase/nf-objidlbase-imalloc-getsize)，以及[CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)。 最大可配置的記憶體數量等於 INT_MAX (2147483647) 位元組。

## <a name="example"></a>範例

範例，請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>需求

**標頭：** ATLComMem.h

##  <a name="allocate"></a>  CComHeap::Allocate

呼叫這個方法來配置記憶體區塊。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*nBytes*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫[ccomheap:: Free](#free)或是[ccomheap:: Reallocate](#reallocate)釋放這個方法所配置的記憶體。

使用實作[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)。

##  <a name="free"></a>  Ccomheap:: Free

呼叫這個方法來釋放此記憶體管理員所配置的記憶體區塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值，且沒有任何作用。

### <a name="remarks"></a>備註

使用實作[CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree)。

##  <a name="getsize"></a>  CComHeap::GetSize

呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

傳回配置的記憶體區塊大小，以位元組為單位。

### <a name="remarks"></a>備註

使用實作[IMalloc::GetSize](/windows/desktop/api/objidlbase/nf-objidlbase-imalloc-getsize)。

##  <a name="reallocate"></a>  Ccomheap:: Reallocate

呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。

*nBytes*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫[ccomheap:: Free](#free)釋放這個方法所配置的記憶體。

使用實作[CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)。

## <a name="see-also"></a>另請參閱

[DynamicConsumer 範例](../../visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap 類別](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
