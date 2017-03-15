---
title: "CHeapPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CHeapPtr
- CHeapPtr
- ATL.CHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 41334cd7497c9e21d1cf047d7ab304864f663758
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptr-class"></a>CHeapPtr 類別
用來管理堆積指標的智慧型指標類別。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T, class Allocator=CCRTAllocator>  
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要儲存在堆積上的物件類型。  
  
 `Allocator`  
 要使用的記憶體配置類別。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CHeapPtr::CHeapPtr](#cheapptr)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHeapPtr::Allocate](#allocate)|呼叫這個方法來儲存物件在堆積上配置記憶體。|  
|[CHeapPtr::Reallocate](#reallocate)|呼叫這個方法來重新配置在堆積上的記憶體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CHeapPtr::operator =](#operator_eq)|指派運算子。|  
  
## <a name="remarks"></a>備註  
 `CHeapPtr`衍生自[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) ，並依預設使用 CRT 常式 (在[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) 來配置和釋放記憶體。 類別[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)可能用來建構一份堆積的指標。 另請參閱[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，它會使用 COM 記憶體配置常式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcore.h  
  
##  <a name="a-nameallocatea--cheapptrallocate"></a><a name="allocate"></a>CHeapPtr::Allocate  
 呼叫這個方法來儲存物件在堆積上配置記憶體。  
  
```
bool Allocate(size_t nElements = 1) throw();
```  
  
### <a name="parameters"></a>參數  
 `nElements`  
 用來計算配置的記憶體數量的項目數目。 預設值為 1。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體已成功則傳回 true 配置失敗 false。  
  
### <a name="remarks"></a>備註  
 用於保留足夠的記憶體來儲存堆積配置常式*nElement*建構函式中定義之型別的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&77;](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]  
  
##  <a name="a-namecheapptra--cheapptrcheapptr"></a><a name="cheapptr"></a>CHeapPtr::CHeapPtr  
 建構函式。  
  
```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 現有的堆積指標或`CHeapPtr`。  
  
### <a name="remarks"></a>備註  
 堆積的指標可以選擇性地建立使用現有的指標，或`CHeapPtr`物件。 如果是的話，新`CHeapPtr`物件負責管理新的指標和資源。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&78;](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]  
  
##  <a name="a-nameoperatoreqa--cheapptroperator-"></a><a name="operator_eq"></a>CHeapPtr::operator =  
 指派運算子。  
  
```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 現有的 `CHeapPtr` 物件。  
  
### <a name="return-value"></a>傳回值  
 傳回參考更新的`CHeapPtr`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&80;](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]  
  
##  <a name="a-namereallocatea--cheapptrreallocate"></a><a name="reallocate"></a>CHeapPtr::Reallocate  
 呼叫這個方法來重新配置在堆積上的記憶體。  
  
```
bool Reallocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>參數  
 `nElements`  
 新項目用來計算配置的記憶體數量的數目。  
  
### <a name="return-value"></a>傳回值  
 如果記憶體已成功則傳回 true 配置失敗 false。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&79;](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CHeapPtrBase 類別](../../atl/reference/cheapptrbase-class.md)   
 [CCRTAllocator 類別](../../atl/reference/ccrtallocator-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

