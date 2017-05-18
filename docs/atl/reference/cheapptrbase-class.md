---
title: "CHeapPtrBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8084104489f6f1e2358ce0cbb573f4e20a0c4fce
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptrbase-class"></a>CHeapPtrBase 類別
這個類別會構成數個堆積的智慧型指標類別的基礎。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要儲存在堆積上的物件類型。  
  
 `Allocator`  
 要使用的記憶體配置類別。 根據預設 CRT 常式用來配置和釋放記憶體。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|呼叫這個方法來配置記憶體。|  
|[CHeapPtrBase::Attach](#attach)|呼叫這個方法來取得現有指標的擁有權。|  
|[CHeapPtrBase::Detach](#detach)|呼叫此方法，以釋放指標的擁有權。|  
|[CHeapPtrBase::Free](#free)|呼叫此方法以刪除所指向的物件`CHeapPtrBase`。|  
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|呼叫這個方法來重新配置記憶體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CHeapPtrBase::operator T *](#operator_t_star)|轉型運算子。|  
|[CHeapPtrBase::operator i](#operator_amp)|I 運算子。|  
|[-> CHeapPtrBase::operator](#operator_ptr)|成員指標運算子。|  

  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CHeapPtrBase::m_pData](#m_pdata)|指標的資料成員變數。|  
  
## <a name="remarks"></a>備註  
 這個類別會構成數個堆積的智慧型指標類別的基礎。 在衍生的類別，例如[CHeapPtr](../../atl/reference/cheapptr-class.md)和[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，加入自己的建構函式和運算子。 請參閱這些類別的實作範例。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcore.h  
  
##  <a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes  
 呼叫這個方法來配置記憶體。  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 記憶體配置的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體成功則傳回 true 配置，false 否則。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果，就會發生判斷提示失敗[CHeapPtrBase::m_pData](#m_pdata)成員變數現在指向現有的值; 也就是說，不等於 NULL。  
  
##  <a name="attach"></a>CHeapPtrBase::Attach  
 呼叫這個方法來取得現有指標的擁有權。  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>參數  
 `pData`  
 `CHeapPtrBase`物件會取得這個指標的擁有權。  
  
### <a name="remarks"></a>備註  
 當`CHeapPtrBase`物件會取得指標的擁有權，則它會自動刪除指標和配置的資料超出範圍時。  
  
 在偵錯組建中，如果，就會發生判斷提示失敗[CHeapPtrBase::m_pData](#m_pdata)成員變數現在指向現有的值; 也就是說，不等於 NULL。  
  
##  <a name="dtor"></a>CHeapPtrBase:: ~ CHeapPtrBase  
 解構函式。  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="detach"></a>CHeapPtrBase::Detach  
 呼叫此方法，以釋放指標的擁有權。  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回指標的複本。  
  
### <a name="remarks"></a>備註  
 釋放指標的擁有權、 設定[CHeapPtrBase::m_pData](#m_pdata)成員變數為 NULL，並傳回指標的複本。  
  
##  <a name="free"></a>CHeapPtrBase::Free  
 呼叫此方法以刪除所指向的物件`CHeapPtrBase`。  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>備註  
 指向物件`CHeapPtrBase`釋出，而[CHeapPtrBase::m_pData](#m_pdata)成員變數設為 NULL。  
  
##  <a name="m_pdata"></a>CHeapPtrBase::m_pData  
 指標的資料成員變數。  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>備註  
 這個成員變數會保留指標資訊。  
  
##  <a name="operator_amp"></a>CHeapPtrBase::operator&amp;  
 I 運算子。  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回所指物件的位址`CHeapPtrBase`物件。  
  

##  <a name="operator_ptr"></a>CHeapPtrBase::operator-&gt;  

 成員指標運算子。  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的值[CHeapPtrBase::m_pData](#m_pdata)成員變數。  
  
### <a name="remarks"></a>備註  
 使用這個運算子所指的類別中呼叫的方法`CHeapPtrBase`物件。 在偵錯組建中，如果，就會發生判斷提示失敗`CHeapPtrBase`點為 NULL。  
  
##  <a name="operator_t_star"></a>CHeapPtrBase::operator T *  
 轉型運算子。  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回[CHeapPtrBase::m_pData](#m_pdata)。  
  
##  <a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes  
 呼叫這個方法來重新配置記憶體。  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBytes`  
 新配置，以位元組為單位的記憶體數量。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體成功則傳回 true 配置，false 否則。  
  
## <a name="see-also"></a>另請參閱  
 [CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr 類別](../../atl/reference/ccomheapptr-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

