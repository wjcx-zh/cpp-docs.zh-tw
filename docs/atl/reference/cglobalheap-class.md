---
title: CGlobalHeap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f3113cf4176c3f582a210e89e732d5e0d92b62d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882828"
---
# <a name="cglobalheap-class"></a>CGlobalHeap 類別
這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 全域堆積函式。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cglobalheap:: Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|  
|[Cglobalheap:: Free](#free)|呼叫這個方法來釋放此記憶體管理員所配置的記憶體區塊。|  
|[CGlobalHeap::GetSize](#getsize)|呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。|  
|[Cglobalheap:: Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 `CGlobalHeap` 實作使用 Win32 全域堆積函式的記憶體配置函式。  
  
> [!NOTE]
>  全域堆積函式會低於其他記憶體管理函式，並不會提供許多功能。 因此，應該使用新的應用程式[堆積函式](http://msdn.microsoft.com/library/windows/desktop/aa366711)。 中會有這些[CWin32Heap](../../atl/reference/cwin32heap-class.md)類別。 全域函式仍會使用 DDE 和剪貼簿函式。  
  
## <a name="example"></a>範例  
 範例，請參閱[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlmem.h  
  
##  <a name="allocate"></a>  Cglobalheap:: Allocate  
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
 呼叫[cglobalheap:: Free](#free)或是[cglobalheap:: Reallocate](#reallocate)釋放這個方法所配置的記憶體。  
  
 使用實作[GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)搭配 GMEM_FIXED 旗標參數。  
  
##  <a name="free"></a>  Cglobalheap:: Free  
 呼叫這個方法來釋放此記憶體管理員所配置的記憶體區塊。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 *p*  
 此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值，且沒有任何作用。  
  
### <a name="remarks"></a>備註  
 使用實作[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)。  
  
##  <a name="getsize"></a>  CGlobalHeap::GetSize  
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
 使用實作[GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593)。  
  
##  <a name="reallocate"></a>  Cglobalheap:: Reallocate  
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
 呼叫[cglobalheap:: Free](#free)釋放這個方法所配置的記憶體。  
  
 使用實作[GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [CComHeap 類別](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap 類別](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)
