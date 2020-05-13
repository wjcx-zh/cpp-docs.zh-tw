---
title: CWin32堆類
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: 2d79de308b1afb3059cf04ad40b63b6e603073c8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746027"
---
# <a name="cwin32heap-class"></a>CWin32堆類

此類使用 Win32 堆分配函數實現[IAtlMemMgr。](../../atl/reference/iatlmemmgr-class.md)

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWin32堆:CWin32Heap](#cwin32heap)|建構函式。|
|[CWin32堆:~CWin32Heap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWin32堆:分配](#allocate)|從堆積物件配置記憶體區塊。|
|[CWin32堆:附加](#attach)|將堆物件附加到現有堆。|
|[CWin32Heap::D埃塔奇](#detach)|從現有堆分離堆物件。|
|[CWin32Heap:免費](#free)|釋放以前從堆中分配的記憶體。|
|[CWin32堆:取得大小](#getsize)|返回從堆物件分配的記憶體塊的大小。|
|[CWin32Heap:重新分配](#reallocate)|從堆積物件重新配置記憶體區塊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CWin32堆::m_bOwnHeap](#m_bownheap)|用於確定堆句柄的當前擁有權的標誌。|
|[CWin32堆:m_hHeap](#m_hheap)|句柄到堆物件。|

## <a name="remarks"></a>備註

`CWin32Heap`使用 Win32 堆分配函數實現記憶體分配方法,包括[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)和[HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)。 與其他堆類不同,`CWin32Heap`要求在分配記憶體之前提供有效的堆句柄:其他類預設使用進程堆。 該句柄可以提供給構造函數或[CWin32Heap::附加](#attach)方法。 有關詳細資訊,請參閱[CWin32Heap::CWin32Heap](#cwin32heap)方法。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>需求

**標題:** atlmem.h

## <a name="cwin32heapallocate"></a><a name="allocate"></a>CWin32堆:分配

從堆積物件配置記憶體區塊。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊的指標。

### <a name="remarks"></a>備註

調用[CWin32Heap::免費](#free)或[CWin32Heap:重新分配](#reallocate)以釋放此方法分配的記憶體。

使用[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)實現 。

## <a name="cwin32heapattach"></a><a name="attach"></a>CWin32堆:附加

將堆物件附加到現有堆。

```cpp
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>參數

*hHeap*<br/>
現有堆句柄。

*b 取得擁有權*<br/>
指示`CWin32Heap`物件是否對堆的資源的擁有權的標誌。

### <a name="remarks"></a>備註

如果*bTake 擁有權*為`CWin32Heap`TRUE,則物件負責刪除堆句柄。

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a>CWin32堆:CWin32Heap

建構函式。

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>參數

*hHeap*<br/>
現有的堆積物件。

*dwFlags*<br/>
建立堆積時使用的旗標。

*nInitialSize*<br/>
堆積的初始大小。

*nMaxSize*<br/>
堆積的大小上限。

### <a name="remarks"></a>備註

在配置記憶體之前，必須先提供包含有效堆積控制代碼的 `CWin32Heap` 物件。 達到這個目的最簡單的方式是使用處理序堆積：

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

另外也可以提供現有的堆積處理代碼給建構函式，在此情況下，新物件不會接收堆積的擁有權。 `CWin32Heap` 物件刪除後，原始堆積控制代碼仍然有效。

可以使用[CWin32Heap::附加](#attach),將現有堆附加到新物件。

如果在作業全部從單一執行緒執行的情況下需要堆積，最好的方式是建立物件，如下所示：

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

HEAP_NO_SERIALIZE 參數會指定，當堆積函式配置和釋放記憶體且效能相應提升時，不使用互斥。

第三個參數預設為 0，如此可讓堆積隨需求擴大。 有關記憶體大小和標誌的說明,請參閱[HeapCreate。](/windows/win32/api/heapapi/nf-heapapi-heapcreate)

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a>CWin32堆:~CWin32Heap

解構函式。

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>備註

如果物件擁有堆的擁有權`CWin32Heap`, 則銷毀堆句柄。

## <a name="cwin32heapdetach"></a><a name="detach"></a>CWin32Heap::D埃塔奇

從現有堆分離堆物件。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>傳回值

將句柄返回到物件以前附加到的堆。

## <a name="cwin32heapfree"></a><a name="free"></a>CWin32Heap:免費

釋放以前由[CWin32Heap](#allocate)從堆中分配的記憶體::分配或[CWin32Heap::重新分配](#reallocate)。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
指標到記憶體塊以釋放。 NULL 是有效的值,不執行任何操作。

## <a name="cwin32heapgetsize"></a><a name="getsize"></a>CWin32堆:取得大小

返回從堆物件分配的記憶體塊的大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
指向該方法將獲取其大小的記憶體塊的指標。 這是[CWin32Heap 傳回的指標::配置](#allocate)或[CWin32Heap::重新分配](#reallocate)。

### <a name="return-value"></a>傳回值

返回已分配記憶體塊的大小(以位元組為單位)。

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a>CWin32堆::m_bOwnHeap

用於確定存儲在[m_hHeap](#m_hheap)中的堆句柄的當前擁有權的標誌。

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a>CWin32堆:m_hHeap

句柄到堆物件。

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>備註

用於將句柄存儲到堆物件的變數。

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a>CWin32Heap:重新分配

從堆積物件重新配置記憶體區塊。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
若要重新配置之記憶體區塊的指標。

*n 位元組*<br/>
配置之區塊的新大小 (以位元組為單位)。 區塊可以放大或縮小。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊的指標。

### <a name="remarks"></a>備註

如果*p*為 NULL,則假定記憶體區尚未分配,[並且 CWin32Heap:: 分配](#allocate)被呼叫,參數為*nBytes*。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)<br/>
[C 本地堆類](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)
