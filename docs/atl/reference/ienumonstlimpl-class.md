---
title: "IEnumOnSTLImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 291993d2914d6082b69bfe7816d7c805e93494c4
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl 類別
這個類別會定義 c + + 標準程式庫集合為基礎的列舉程式介面。  
  
## <a name="syntax"></a>語法  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 COM 列舉值 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 介面。  
  
 `piid`  
 列舉程式介面的介面 ID 的指標。  
  
 `T`  
 列舉程式介面所公開的項目類型。  
  
 `Copy`  
 A[複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
 `CollType`  
 C + + 標準程式庫容器類別。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|實作[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)。|  
|[IEnumOnSTLImpl::Init](#init)|初始化列舉值。|  
|[IEnumOnSTLImpl::Next](#next)|實作[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)。|  
|[IEnumOnSTLImpl::Reset](#reset)|實作[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)。|  
|[IEnumOnSTLImpl::Skip](#skip)|實作[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|迭代器，表示集合中的列舉值的目前位置。|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|存放要列舉的項目之 c + + 標準程式庫容器指標。|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|**IUnknown**提供集合物件的指標。|  
  
## <a name="remarks"></a>備註  
 `IEnumOnSTLImpl`提供列舉的項目中的 c + + 標準程式庫相容容器的儲存位置的 COM 列舉程式介面的實作。 這個類別是類似於[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)類別，可提供列舉值介面的實作，根據陣列。  
  
> [!NOTE]
>  請參閱[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)進一步之間差異的詳細資訊如`CComEnumImpl`和`IEnumOnSTLImpl`。  
  
 一般而言，您將*不*必須建立您自己的列舉值類別衍生自這個介面的實作。 如果您想要使用 c + + 標準程式庫容器為基礎的 ATL 提供列舉值，比較常見建立的執行個體是[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)，或是建立衍生自所傳回的列舉值的集合類別[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。  
  
 不過，如果您需要提供自訂的列舉值 （例如，一個公開除了列舉程式介面的介面），您可以從這個類別衍生。 在這種情況下很可能必須覆寫[複製](#clone)方法，以提供您自己的實作。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="init"></a>IEnumOnSTLImpl::Init  
 初始化列舉值。  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>參數  
 `pUnkForRelease`  
 [in]**IUnknown**必須保持存留在生命週期的列舉值物件的指標。 傳遞**NULL**如果物件不存在。  
  
 `collection`  
 C + + 標準程式庫容器，包含要列舉的項目參考。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果您傳遞`Init`集合的參考保留在另一個物件，您可以使用`pUnkForRelease`參數，以確保物件和集合，它會保留，可用的只要列舉值需要它。  
  
 您必須呼叫這個方法之前將指標傳遞給任何用戶端的列舉程式介面。  
  
##  <a name="clone"></a>IEnumOnSTLImpl::Clone  
 這個方法提供實作[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)方法藉由建立型別的物件`CComEnumOnSTL`，初始化具有相同的集合和迭代器使用目前的物件，並傳回新建立的物件上的介面。  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]從目前的列舉值會複製新建立的物件上的列舉程式介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk  
 **IUnknown**提供集合物件的指標。  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>備註  
 這個智慧型指標會維持物件傳遞至參考[IEnumOnSTLImpl::Init](#init)，確保它運作的列舉值的存留期間。  
  
##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection  
 這個成員會指向提供資料驅動型的列舉值介面實作的集合。  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>備註  
 這個成員由呼叫初始化[IEnumOnSTLImpl::Init](#init)。  
  
##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter  
 這個成員會保留用來標示集合中目前的位置，並瀏覽至後續元素的迭代器。  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>IEnumOnSTLImpl::Next  
 這個方法提供實作[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)方法。  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>參數  
 `celt`  
 [in]要求的項目數目。  
  
 `rgelt`  
 [out]要填入之項目的陣列。  
  
 `pceltFetched`  
 [out]中實際傳回的元素數目`rgelt`。 這可以是小於`celt`如果少於`celt`仍然在清單中的項目。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="reset"></a>IEnumOnSTLImpl::Reset  
 這個方法提供實作[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)方法。  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="skip"></a>IEnumOnSTLImpl::Skip  
 這個方法提供實作[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)方法。  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>參數  
 `celt`  
 [in]略過的項目數目。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

