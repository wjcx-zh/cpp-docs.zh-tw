---
title: CWin32Heap 類別
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
ms.openlocfilehash: ce3585310198ee3e2d7b2b8b829f4202b1021284
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496207"
---
# <a name="cwin32heap-class"></a>CWin32Heap 類別

這個類別會使用 Win32 堆積配置函數來執行[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) 。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWin32Heap:: CWin32Heap](#cwin32heap)|建構函式。|
|[CWin32Heap:: ~ CWin32Heap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CWin32Heap::Allocate](#allocate)|從堆積物件配置記憶體區塊。|
|[CWin32Heap::Attach](#attach)|將堆積物件附加至現有的堆積。|
|[CWin32Heap::Detach](#detach)|從現有堆積卸離堆積物件。|
|[CWin32Heap:: Free](#free)|釋放先前從堆積配置的記憶體。|
|[CWin32Heap::GetSize](#getsize)|傳回從堆積物件配置的記憶體區塊大小。|
|[CWin32Heap::Reallocate](#reallocate)|從堆積物件重新配置記憶體區塊。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|用來判斷堆積控制碼目前擁有權的旗標。|
|[CWin32Heap::m_hHeap](#m_hheap)|堆積物件的控制碼。|

## <a name="remarks"></a>備註

`CWin32Heap`使用 Win32 堆積配置函數 (包括[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)和[HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)) 來執行記憶體配置方法。 不同于其他堆積類別`CWin32Heap` , 需要在配置記憶體之前提供有效的堆積控制碼: 其他類別預設為使用進程堆積。 控制碼可以提供給函式或[CWin32Heap:: Attach](#attach)方法。 如需詳細資訊, 請參閱[CWin32Heap:: CWin32Heap](#cwin32heap)方法。

## <a name="example"></a>範例

請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)的範例。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>需求

**標頭:** atlmem。h

##  <a name="allocate"></a>CWin32Heap:: Allocate

從堆積物件配置記憶體區塊。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*nBytes*<br/>
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊的指標。

### <a name="remarks"></a>備註

呼叫[CWin32Heap:: Free](#free)或[CWin32Heap::](#reallocate)重新配置以釋放這個方法所配置的記憶體。

使用[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)來執行。

##  <a name="attach"></a>CWin32Heap:: Attach

將堆積物件附加至現有的堆積。

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>參數

*hHeap*<br/>
現有的堆積控制碼。

*bTakeOwnership*<br/>
旗標, 指出`CWin32Heap`物件是否要取得堆積資源的擁有權。

### <a name="remarks"></a>備註

如果*bTakeOwnership*為 TRUE, 則`CWin32Heap`物件會負責刪除堆積控制碼。

##  <a name="cwin32heap"></a>CWin32Heap:: CWin32Heap

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

現有的堆積也可以附加至新的物件, 使用[CWin32Heap:: Attach](#attach)。

如果在作業全部從單一執行緒執行的情況下需要堆積，最好的方式是建立物件，如下所示：

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

參數 HEAP_NO_SERIALIZE 指定當堆積函式配置和釋放記憶體時, 將不會使用互斥, 並以效能增加為依據。

第三個參數預設為 0，如此可讓堆積隨需求擴大。 如需記憶體大小和旗標的說明, 請參閱[HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) 。

##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap

解構函式。

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>備註

當`CWin32Heap`物件具有堆積的擁有權時, 終結堆積控制碼。

##  <a name="detach"></a>CWin32Heap::D etach

從現有堆積卸離堆積物件。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回物件先前附加之堆積的控制碼。

##  <a name="free"></a>CWin32Heap:: Free

藉由[CWin32Heap:: Allocate](#allocate)或[CWin32Heap::](#reallocate)重新配置, 釋放先前從堆積配置的記憶體。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
要釋放的記憶體區塊的指標。 Null 是有效的值, 不會執行任何操作。

##  <a name="getsize"></a>CWin32Heap:: GetSize

傳回從堆積物件配置的記憶體區塊大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
此方法將取得其大小之記憶體區塊的指標。 這是[CWin32Heap:: Allocate](#allocate)或[CWin32Heap::](#reallocate)重新配置所傳回的指標。

### <a name="return-value"></a>傳回值

傳回已配置記憶體區塊的大小 (以位元組為單位)。

##  <a name="m_bownheap"></a>CWin32Heap:: m_bOwnHeap

用來判斷[m_hHeap](#m_hheap)中儲存之堆積控制碼目前擁有權的旗標。

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>CWin32Heap:: m_hHeap

堆積物件的控制碼。

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>備註

用來儲存堆積物件之控制碼的變數。

##  <a name="reallocate"></a>CWin32Heap:: 重新配置

從堆積物件重新配置記憶體區塊。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
若要重新配置之記憶體區塊的指標。

*nBytes*<br/>
配置之區塊的新大小 (以位元組為單位)。 區塊可以放大或縮小。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊的指標。

### <a name="remarks"></a>備註

如果*p*是 Null, 則會假設尚未配置記憶體區塊, 而且會呼叫[CWin32Heap:: Allocate](#allocate) , 並具有*nBytes*的引數。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap 類別](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap 類別](../../atl/reference/ccomheap-class.md)
