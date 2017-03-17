---
title: "CComHeap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 323ad1aed4bae706ecbf66de769e33873f20c149
ms.lasthandoff: 02/24/2017

---
# <a name="ccomheap-class"></a>CComHeap 類別
這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 COM 記憶體配置函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComHeap::Allocate](#allocate)|呼叫這個方法來配置記憶體區塊。|  
|[CComHeap::Free](#free)|呼叫此方法以釋放此記憶體管理員所配置的記憶體區塊。|  
|[CComHeap::GetSize](#getsize)|呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。|  
|[CComHeap::Reallocate](#reallocate)|呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 `CComHeap`實作記憶體配置函式使用 COM 配置功能，包括[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)， [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)， [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)，和[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)。 可配置的記憶體數量上限等於**INT_MAX** (2147483647) 個位元組。  
  
## <a name="example"></a>範例  
 請參閱範例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ATLComMem.h  
  
##  <a name="allocate"></a>CComHeap::Allocate  
 呼叫這個方法來配置記憶體區塊。  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[CComHeap::Free](#free)或[CComHeap::Reallocate](#reallocate)釋放透過這個方法配置的記憶體。  
  
 使用實作[CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727)。  
  
##  <a name="free"></a>CComHeap::Free  
 呼叫此方法以釋放此記憶體管理員所配置的記憶體區塊。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 此記憶體管理員先前所配置之記憶體的指標。 NULL 是有效的值，並不執行任何動作。  
  
### <a name="remarks"></a>備註  
 使用實作[CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722)。  
  
##  <a name="getsize"></a>CComHeap::GetSize  
 呼叫這個方法，以取得此記憶體管理員所配置的記憶體區塊配置的大小。  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 此記憶體管理員先前所配置之記憶體的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回配置的記憶體區塊大小，以位元組為單位。  
  
### <a name="remarks"></a>備註  
 使用實作[IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)。  
  
##  <a name="reallocate"></a>CComHeap::Reallocate  
 呼叫這個方法來重新配置此記憶體管理員所配置的記憶體。  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 此記憶體管理員先前所配置之記憶體的指標。  
  
 `nBytes`  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊開頭的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[CComHeap::Free](#free)釋放透過這個方法配置的記憶體。  
  
 使用實作[CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)。  
  
## <a name="see-also"></a>另請參閱  
 [DynamicConsumer 範例](../../visual-cpp-samples.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [CWin32Heap 類別](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap 類別](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)

