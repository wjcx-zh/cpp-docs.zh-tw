---
title: "CWin32Heap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
caps.latest.revision: 19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 407f777b52529a333251c7d00481fdbfb14db619
ms.lasthandoff: 02/24/2017

---
# <a name="cwin32heap-class"></a>CWin32Heap 類別
這個類別會實作[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)使用 Win32 堆積配置函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CWin32Heap : public IAtlMemMgr
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWin32Heap::CWin32Heap](#cwin32heap)|建構函式。|  
|[CWin32Heap:: ~ CWin32Heap](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWin32Heap::Allocate](#allocate)|從堆積物件配置記憶體區塊。|  
|[Cwin32heap:: Attach](#attach)|將堆積物件附加至現有的堆積。|  
|[CWin32Heap::Detach](#detach)|中斷連結現有的堆積中的堆積物件。|  
|[CWin32Heap::Free](#free)|釋放先前配置的堆積記憶體。|  
|[CWin32Heap::GetSize](#getsize)|傳回從堆積的物件配置的記憶體區塊的大小。|  
|[CWin32Heap::Reallocate](#reallocate)|從堆積物件重新配置記憶體區塊。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|旗標，用來判斷目前的擁有權的堆積控制代碼。|  
|[CWin32Heap::m_hHeap](#m_hheap)|堆積物件控制代碼。|  
  
## <a name="remarks"></a>備註  
 `CWin32Heap`實作使用 Win32 堆積配置函式，包括記憶體配置方法[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)和[HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701)。 不同於其他堆積的類別，`CWin32Heap`需要配置記憶體之前，必須提供有效堆積控制代碼︰ 其他類別預設為使用處理序堆積。 建構函式，或寫入控制代碼可提供[cwin32heap:: Attach](#attach)方法。 請參閱[CWin32Heap::CWin32Heap](#cwin32heap)方法，如需詳細資訊。  
  
## <a name="example"></a>範例  
 請參閱範例[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlmem.h  
  
##  <a name="allocate"></a>CWin32Heap::Allocate  
 從堆積物件配置記憶體區塊。  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 在新記憶體區塊中要求的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊的指標。  
  
### <a name="remarks"></a>備註  
 呼叫[CWin32Heap::Free](#free)或[CWin32Heap::Reallocate](#reallocate)釋放透過這個方法配置的記憶體。  
  
 使用實作[HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597)。  
  
##  <a name="attach"></a>Cwin32heap:: Attach  
 將堆積物件附加至現有的堆積。  
  
```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```  
  
### <a name="parameters"></a>參數  
 `hHeap`  
 現有的堆積控制代碼。  
  
 `bTakeOwnership`  
 旗標，指出如果`CWin32Heap`物件是堆積的資源取得擁有權。  
  
### <a name="remarks"></a>備註  
 如果`bTakeOwnership`為 TRUE，`CWin32Heap`物件會刪除，堆積控制代碼。  
  
##  <a name="cwin32heap"></a>CWin32Heap::CWin32Heap  
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
 `hHeap`  
 現有的堆積物件。  
  
 `dwFlags`  
 建立堆積時使用的旗標。  
  
 *nInitialSize*  
 堆積的初始大小。  
  
 `nMaxSize`  
 堆積的大小上限。  
  
### <a name="remarks"></a>備註  
 在配置記憶體之前，必須先提供包含有效堆積控制代碼的 `CWin32Heap` 物件。 達到這個目的最簡單的方式是使用處理序堆積：  
  
 [!code-cpp[NVC_ATL_Utilities #&92;](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]  
  
 另外也可以提供現有的堆積處理代碼給建構函式，在此情況下，新物件不會接收堆積的擁有權。 `CWin32Heap` 物件刪除後，原始堆積控制代碼仍然有效。  
  
 也可以將現有的堆積附加至新物件、 使用[cwin32heap:: Attach](#attach)。  
  
 如果在作業全部從單一執行緒執行的情況下需要堆積，最好的方式是建立物件，如下所示：  
  
 [!code-cpp[NVC_ATL_Utilities #&93;](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]  
  
 參數**HEAP_NO_SERIALIZE**指定堆積函式配置和釋放記憶體，且效能時，不會使用互斥。  
  
 第三個參數預設為 0，如此可讓堆積隨需求擴大。 請參閱[HeapCreate](http://msdn.microsoft.com/library/windows/desktop/aa366599\(v=vs.85\).aspx)的記憶體大小和旗標的說明。  
  
##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap  
 解構函式。  
  
```
~CWin32Heap() throw();
```  
  
### <a name="remarks"></a>備註  
 終結的堆積控制代碼，如果`CWin32Heap`物件具有堆積的擁有權。  
  
##  <a name="detach"></a>CWin32Heap::Detach  
 中斷連結現有的堆積中的堆積物件。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的堆積的物件先前附加的控制代碼。  
  
##  <a name="free"></a>CWin32Heap::Free  
 釋放先前配置的堆積中[CWin32Heap::Allocate](#allocate)或[CWin32Heap::Reallocate](#reallocate)。  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 要釋放的記憶體區塊指標。 NULL 是有效的值，並不執行任何動作。  
  
##  <a name="getsize"></a>CWin32Heap::GetSize  
 傳回從堆積的物件配置的記憶體區塊的大小。  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 記憶體區塊的方法會取得其大小的指標。 這是所傳回的指標[CWin32Heap::Allocate](#allocate)或[CWin32Heap::Reallocate](#reallocate)。  
  
### <a name="return-value"></a>傳回值  
 傳回大小，以位元組為單位配置的記憶體區塊。  
  
##  <a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap  
 旗標，用來判斷目前的擁有權的堆積控制代碼儲存在[m_hHeap](#m_hheap)。  
  
```
bool m_bOwnHeap;
```  
  
##  <a name="m_hheap"></a>CWin32Heap::m_hHeap  
 堆積物件控制代碼。  
  
```
HANDLE m_hHeap;
```  
  
### <a name="remarks"></a>備註  
 變數，用來儲存堆積物件的控制代碼。  
  
##  <a name="reallocate"></a>CWin32Heap::Reallocate  
 從堆積物件重新配置記憶體區塊。  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 若要重新配置之記憶體區塊的指標。  
  
 `nBytes`  
 配置之區塊的新大小 (以位元組為單位)。 區塊可以放大或縮小。  
  
### <a name="return-value"></a>傳回值  
 傳回新配置記憶體區塊的指標。  
  
### <a name="remarks"></a>備註  
 如果`p`是 NULL，則會假設尚未配置的記憶體區塊和[CWin32Heap::Allocate](#allocate)呼叫時，使用引數`nBytes`。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [IAtlMemMgr 類別](../../atl/reference/iatlmemmgr-class.md)   
 [CLocalHeap 類別](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap 類別](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap 類別](../../atl/reference/ccrtheap-class.md)   
 [CComHeap 類別](../../atl/reference/ccomheap-class.md)

