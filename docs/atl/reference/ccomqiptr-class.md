---
title: "CComQIPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b63e584b7c4620be0e77da034a2a419b80cf741
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomqiptr-class"></a>CComQIPtr 類別
用來管理 COM 介面指標的智慧型指標類別。  
  
## <a name="syntax"></a>語法  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 指定要儲存的指標類型的 COM 介面。  
  
 `piid`  
 指向 IID 的`T`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|建構函式。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|將指標指派給成員指標。|  
  
## <a name="remarks"></a>備註  
 使用 ATL`CComQIPtr`和[CComPtr](../../atl/reference/ccomptr-class.md)來管理 COM 介面指標，這兩者都衍生自[CComPtrBase](../../atl/reference/ccomptrbase-class.md)。 這兩個類別執行自動參考計數透過呼叫`AddRef`和**發行**。 多載的運算子處理指標作業。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>CComQIPtr::CComQIPtr  
 建構函式。  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>參數  
 `lp`  
 用來初始化的介面指標。  
  
 `T`  
 COM 介面。  
  
 `piid`  
 指向 IID 的`T`。  
  
##  <a name="operator_eq"></a>CComQIPtr::operator =  
 指派運算子。  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>參數  
 `lp`  
 用來初始化的介面指標。  
  
 `T`  
 COM 介面。  
  
 `piid`  
 指向 IID 的`T`。  
  
### <a name="return-value"></a>傳回值  
 讓指標回到更新`CComQIPtr`物件。  
  
## <a name="see-also"></a>請參閱  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [CComPtrBase 類別](../../atl/reference/ccomptrbase-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)
