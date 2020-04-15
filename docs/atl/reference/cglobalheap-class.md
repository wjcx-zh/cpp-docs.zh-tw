---
title: CGlobalHeap 類別
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326946"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 類別

此類使用 Win32 全域堆函數實現[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGlobalHeap:分配](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CGlobalHeap:免費](#free)|調用此方法以釋放此記憶體管理員分配的記憶體塊。|
|[CGlobalHeap:取得大小](#getsize)|呼叫此方法獲取此記憶體管理員分配的記憶體區塊的分配大小。|
|[CGlobalHeap:重新分配](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CGlobalHeap`使用 Win32 全域堆函數實現記憶體分配函數。

> [!NOTE]
> 全域堆函數比其他記憶體管理函數慢,並且不提供盡可能多的功能。 因此,新應用程式應使用[堆函數](/windows/win32/Memory/heap-functions)。 這些在[CWin32Heap](../../atl/reference/cwin32heap-class.md)類中可用。 DDE 和剪貼簿函數仍使用全域函數。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>需求

**標題:** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap:分配

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

調用[CGlobalHeap::免費](#free)或[CGlobalHeap:重新分配](#reallocate)以釋放此方法分配的記憶體。

使用帶有GMEM_FIXED標誌參數的[Global Alloc](/windows/win32/api/winbase/nf-winbase-globalalloc)實現。

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap:免費

調用此方法以釋放此記憶體管理員分配的記憶體塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值,不執行任何操作。

### <a name="remarks"></a>備註

使用[GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)實作 。

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap:取得大小

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

使用[全域大小](/windows/win32/api/winbase/nf-winbase-globalsize)。

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap:重新分配

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

調用[CGlobalHeap::可自由](#free)釋放此方法分配的記憶體。

使用[GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)實現。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)<br/>
[CWin32堆類](../../atl/reference/cwin32heap-class.md)<br/>
[C 本地堆類](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap 類](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
