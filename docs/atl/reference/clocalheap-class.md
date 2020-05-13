---
title: C 本地堆類
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 303e3b85ad11c309f862f59d6ec610701c4ef6db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326764"
---
# <a name="clocalheap-class"></a>C 本地堆類

此類使用 Win32 本地堆函數實現[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CLocalHeap:分配](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CLocalHeap:免費](#free)|調用此方法以釋放此記憶體管理員分配的記憶體塊。|
|[CLocalHeap:取得大小](#getsize)|呼叫此方法獲取此記憶體管理員分配的記憶體區塊的分配大小。|
|[CLocalHeap:重新分配](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CLocalHeap`使用 Win32 本地堆函數實現記憶體分配函數。

> [!NOTE]
> 本地堆函數比其他記憶體管理函數慢,並且不提供盡可能多的功能。 因此,新應用程式應使用[堆函數](/windows/win32/Memory/heap-functions)。 這些在[CWin32Heap](../../atl/reference/cwin32heap-class.md)類中可用。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>需求

**標題:** atlmem.h

## <a name="clocalheapallocate"></a><a name="allocate"></a>CLocalHeap:分配

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

調用[CLocalHeap::免費](#free)或[ClocalHeap:重新分配](#reallocate)以釋放此方法分配的記憶體。

使用帶有LMEM_FIXED標誌參數的[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)實現。

## <a name="clocalheapfree"></a><a name="free"></a>CLocalHeap:免費

調用此方法以釋放此記憶體管理員分配的記憶體塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值,不執行任何操作。

### <a name="remarks"></a>備註

使用[本地自由](/windows/win32/api/winbase/nf-winbase-localfree)實作 。

## <a name="clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap:取得大小

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

使用[本地大小](/windows/win32/api/winbase/nf-winbase-localsize)。

## <a name="clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap:重新分配

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

調用[CLocalHeap::可自由](#free)釋放此方法分配的記憶體。

使用[本地ReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc)實現。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)<br/>
[CWin32堆類](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
