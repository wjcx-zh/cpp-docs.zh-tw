---
title: CCRTHeap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5244990d720cd36e0a040e9243067e49716d2549
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754757"
---
# <a name="ccrtheap-class"></a>CCRTHeap 類別

這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 CRT 堆積函式。

## <a name="syntax"></a>語法

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Ccrtheap:: Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|
|[Ccrtheap:: Free](#free)|呼叫這個方法來釋放此記憶體管理員所配置的記憶體區塊。|
|[CCRTHeap::GetSize](#getsize)|呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。|
|[Ccrtheap:: Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|

## <a name="remarks"></a>備註

`CCRTHeap` 實作記憶體配置函式使用 CRT 堆積函式，包括[malloc](../../c-runtime-library/reference/malloc.md)，[免費](../../c-runtime-library/reference/free.md)， [realloc](../../c-runtime-library/reference/realloc.md)，以及[_msize](../../c-runtime-library/reference/msize.md)。

## <a name="example"></a>範例

範例，請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>需求

**標頭：** atlmem.h

##  <a name="allocate"></a>  Ccrtheap:: Allocate

呼叫這個方法來配置記憶體區塊。

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*nBytes*  
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫[ccrtheap:: Free](#free)或是[ccrtheap:: Reallocate](#reallocate)釋放這個方法所配置的記憶體。

使用實作[malloc](../../c-runtime-library/reference/malloc.md)。

##  <a name="free"></a>  Ccrtheap:: Free

呼叫這個方法來釋放此記憶體管理員所配置的記憶體區塊。

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>參數

*p*  
此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值，且沒有任何作用。

### <a name="remarks"></a>備註

使用實作[免費](../../c-runtime-library/reference/free.md)。

##  <a name="getsize"></a>  CCRTHeap::GetSize

呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>參數

*p*  
此記憶體管理員先前所配置之記憶體的指標。

### <a name="return-value"></a>傳回值

傳回配置的記憶體區塊大小，以位元組為單位。

### <a name="remarks"></a>備註

使用實作[_msize](../../c-runtime-library/reference/msize.md)。

##  <a name="reallocate"></a>  Ccrtheap:: Reallocate

呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>參數

*p*  
此記憶體管理員先前所配置之記憶體的指標。

*nBytes*  
在新記憶體區塊中要求的位元組數目。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫[ccrtheap:: Free](#free)釋放這個方法所配置的記憶體。 使用實作[realloc](../../c-runtime-library/reference/realloc.md)。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)   
[CComHeap 類別](../../atl/reference/ccomheap-class.md)   
[CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)   
[CLocalHeap 類別](../../atl/reference/clocalheap-class.md)   
[CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)   
[IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
