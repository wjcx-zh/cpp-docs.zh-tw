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
ms.openlocfilehash: a38d1147e718870c03af84ec1487e226805b956e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327826"
---
# <a name="ccomheap-class"></a>CComHeap 類別

此類使用 COM 記憶體分配函數實現[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComHeap:分配](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CComHeap:免費](#free)|調用此方法以釋放此記憶體管理員分配的記憶體塊。|
|[CComHeap:取得 Size](#getsize)|呼叫此方法獲取此記憶體管理員分配的記憶體區塊的分配大小。|
|[CComHeap:重新分配](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CComHeap`使用 COM 分配函數實現記憶體分配函數,包括 CoTaskMemAlloc、CoTaskMemFree、IMalloc::getSize 和[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)。 [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize) 可分配的記憶體的最大量等於INT_MAX (2147483647) 位元組。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>需求

**標題:** ATLComMem.h

## <a name="ccomheapallocate"></a><a name="allocate"></a>CComHeap:分配

呼叫這個方法來配置記憶體區塊。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

調用[CComHeap:免費](#free)或[CComHeap:重新分配](#reallocate)以釋放此方法分配的記憶體。

使用[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)實現。

## <a name="ccomheapfree"></a><a name="free"></a>CComHeap:免費

調用此方法以釋放此記憶體管理員分配的記憶體塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值,不執行任何操作。

### <a name="remarks"></a>備註

使用[CoTaskMemFree 。](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)

## <a name="ccomheapgetsize"></a><a name="getsize"></a>CComHeap:取得 Size

呼叫此方法獲取此記憶體管理員分配的記憶體區塊的分配大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

返回以位元組為單位的分配記憶體區塊的大小。

### <a name="remarks"></a>備註

使用[IMalloc 取得:取得 Size](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)。

## <a name="ccomheapreallocate"></a><a name="reallocate"></a>CComHeap:重新分配

呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。

*n 位元組*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

調用[CComHeap:免費](#free)釋放此方法分配的記憶體。

使用[CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)實現。

## <a name="see-also"></a>另請參閱

[動態消費者範例](../../overview/visual-cpp-samples.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CWin32堆類](../../atl/reference/cwin32heap-class.md)<br/>
[C 本地堆類](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
