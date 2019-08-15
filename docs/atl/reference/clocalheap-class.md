---
title: CLocalHeap 類別
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
ms.openlocfilehash: a302ba4ea55c42ce214c8de4a24be843d6cb1b9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496752"
---
# <a name="clocalheap-class"></a>CLocalHeap 類別

這個類別會使用 Win32 本機堆積函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[CLocalHeap::Free](#free)|呼叫這個方法以釋放此記憶體管理員所配置的記憶體區塊。|
|[CLocalHeap::GetSize](#getsize)|呼叫這個方法, 以取得此記憶體管理員所配置之記憶體區塊的配置大小。|
|[CLocalHeap::Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CLocalHeap`使用 Win32 本機堆積函數來執行記憶體配置函數。

> [!NOTE]
>  本機堆積函數的速度比其他記憶體管理函式慢, 而且不提供許多功能。 因此, 新的應用程式應該使用[堆積函數](/windows/win32/Memory/heap-functions)。 這些是在[CWin32Heap](../../atl/reference/cwin32heap-class.md)類別中提供。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>需求

**標頭:** atlmem。h

##  <a name="allocate"></a>CLocalHeap:: Allocate

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

呼叫[CLocalHeap:: Free](#free)或[CLocalHeap::](#reallocate)重新配置以釋放這個方法所配置的記憶體。

使用[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)搭配 LMEM_FIXED 的旗標參數來執行。

##  <a name="free"></a>CLocalHeap:: Free

呼叫這個方法以釋放此記憶體管理員所配置的記憶體區塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此記憶體管理員先前所配置之記憶體的指標。 Null 是有效的值, 不會執行任何操作。

### <a name="remarks"></a>備註

使用[LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)來執行。

##  <a name="getsize"></a>CLocalHeap:: GetSize

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

使用[LocalSize](/windows/win32/api/winbase/nf-winbase-localsize)來執行。

##  <a name="reallocate"></a>CLocalHeap:: 重新配置

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

呼叫[CLocalHeap:: free](#free)以釋放這個方法所配置的記憶體。

使用[LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc)來執行。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
