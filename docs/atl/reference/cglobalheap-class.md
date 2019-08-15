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
ms.openlocfilehash: 2b5aa09357ddcc77b6b10de58545bea86eff2488
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496755"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 類別

這個類別會使用 Win32 全域堆積函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGlobalHeap::Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CGlobalHeap::Free](#free)|呼叫這個方法以釋放此記憶體管理員所配置的記憶體區塊。|
|[CGlobalHeap::GetSize](#getsize)|呼叫這個方法, 以取得此記憶體管理員所配置之記憶體區塊的配置大小。|
|[CGlobalHeap::Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CGlobalHeap`使用 Win32 全域堆積函數來執行記憶體配置函數。

> [!NOTE]
>  全域堆積函數的速度會比其他記憶體管理函式慢, 而且不會提供許多功能。 因此, 新的應用程式應該使用[堆積函數](/windows/win32/Memory/heap-functions)。 這些是在[CWin32Heap](../../atl/reference/cwin32heap-class.md)類別中提供。 全域函式仍然由 DDE 和剪貼簿函式使用。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>需求

**標頭:** atlmem。h

##  <a name="allocate"></a>CGlobalHeap:: Allocate

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

呼叫[CGlobalHeap:: Free](#free)或[CGlobalHeap::](#reallocate)重新配置以釋放這個方法所配置的記憶體。

使用[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)搭配 GMEM_FIXED 的旗標參數來執行。

##  <a name="free"></a>CGlobalHeap:: Free

呼叫這個方法以釋放此記憶體管理員所配置的記憶體區塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。 Null 是有效的值, 不會執行任何操作。

### <a name="remarks"></a>備註

使用[GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)來執行。

##  <a name="getsize"></a>CGlobalHeap:: GetSize

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

使用[GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize)來執行。

##  <a name="reallocate"></a>CGlobalHeap:: 重新配置

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

呼叫[CGlobalHeap:: free](#free)以釋放這個方法所配置的記憶體。

使用[GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)來執行。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap 類別](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
