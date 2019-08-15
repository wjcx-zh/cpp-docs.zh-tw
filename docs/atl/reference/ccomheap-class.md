---
title: CComHeap 類別
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: 1ded73047b895a44a22bdd5730886f7fc088c77a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497339"
---
# <a name="ccomheap-class"></a>CComHeap 類別

這個類別會使用 COM 記憶體配置函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComHeap::Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CComHeap:: Free](#free)|呼叫這個方法以釋放此記憶體管理員所配置的記憶體區塊。|
|[CComHeap::GetSize](#getsize)|呼叫這個方法, 以取得此記憶體管理員所配置之記憶體區塊的配置大小。|
|[CComHeap::Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CComHeap`使用 COM 配置函數 (包括[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)、 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)、 [IMalloc:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)和[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)) 來執行記憶體配置函式。 可以配置的記憶體數量上限等於 INT_MAX (2147483647) 個位元組。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>需求

**標頭：** ATLComMem.h

##  <a name="allocate"></a>CComHeap:: Allocate

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

呼叫[CComHeap:: Free](#free)或[CComHeap::](#reallocate)重新配置以釋放這個方法所配置的記憶體。

使用[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)來執行。

##  <a name="free"></a>CComHeap:: Free

呼叫這個方法以釋放此記憶體管理員所配置的記憶體區塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。 Null 是有效的值, 不會執行任何操作。

### <a name="remarks"></a>備註

使用[CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)來執行。

##  <a name="getsize"></a>CComHeap:: GetSize

呼叫這個方法, 以取得此記憶體管理員所配置之記憶體區塊的配置大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

傳回已配置記憶體區塊的大小 (以位元組為單位)。

### <a name="remarks"></a>備註

使用[IMalloc:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)來執行。

##  <a name="reallocate"></a>CComHeap:: 重新配置

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

呼叫[CComHeap:: free](#free)以釋放這個方法所配置的記憶體。

使用[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)來執行。

## <a name="see-also"></a>另請參閱

[DynamicConsumer 範例](../../overview/visual-cpp-samples.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap 類別](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
