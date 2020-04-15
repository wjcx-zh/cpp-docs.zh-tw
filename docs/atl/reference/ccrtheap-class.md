---
title: CCRTHeap 類
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327167"
---
# <a name="ccrtheap-class"></a>CCRTHeap 類

此類使用 CRT 堆函數實現[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

## <a name="syntax"></a>語法

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCRTHeap:分配](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CCRTHeap:免費](#free)|調用此方法以釋放此記憶體管理員分配的記憶體塊。|
|[CCRTHeap:取得大小](#getsize)|呼叫此方法獲取此記憶體管理員分配的記憶體區塊的分配大小。|
|[CCRTHeap:重新分配](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CCRTHeap`使用 CRT 堆函數實現記憶體分配函數,包括[malloc、](../../c-runtime-library/reference/malloc.md)[自由](../../c-runtime-library/reference/free.md)、[真實](../../c-runtime-library/reference/realloc.md)和[_msize。](../../c-runtime-library/reference/msize.md)

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>需求

**標題:** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeap:分配

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

調用[CCRTHeap::免費](#free)或[CCRTHeap:重新分配](#reallocate)以釋放此方法分配的記憶體。

使用[malloc](../../c-runtime-library/reference/malloc.md)實現。

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeap:免費

調用此方法以釋放此記憶體管理員分配的記憶體塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值,不執行任何操作。

### <a name="remarks"></a>備註

使用[免費](../../c-runtime-library/reference/free.md)實現。

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeap:取得大小

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

使用[_msize](../../c-runtime-library/reference/msize.md)實現。

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeap:重新分配

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

調用[CCRTHeap::免費](#free)釋放此方法分配的記憶體。 使用[realloc](../../c-runtime-library/reference/realloc.md)實現。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)<br/>
[CWin32堆類](../../atl/reference/cwin32heap-class.md)<br/>
[C 本地堆類](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
