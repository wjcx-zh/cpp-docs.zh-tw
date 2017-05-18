---
title: "CComEnumImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
dev_langs:
- C++
helpviewer_keywords:
- CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6dc6a8ed6a318642efe58dfb94835d45b2163b54
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomenumimpl-class"></a>CComEnumImpl 類別
這個類別會提供列舉的項目儲存在陣列中的 COM 列舉程式介面的實作。  
  
## <a name="syntax"></a>語法  
  
```
template <class Base,
    const IID* piid, class T, class Copy>  
class ATL_NO_VTABLE CComEnumImpl : public Base
```  
  
#### <a name="parameters"></a>參數  
 `Base`  
 COM 列舉值 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 介面。  
  
 `piid`  
 列舉程式介面的介面 ID 的指標。  
  
 `T`  
 列舉程式介面所公開的項目類型。  
  
 `Copy`  
 同質[複製原則類別](../../atl/atl-copy-policy-classes.md)。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|建構函式。|  
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComEnumImpl::Clone](#clone)|實作[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)。|  
|[CComEnumImpl::Init](#init)|初始化列舉值。|  
|[CComEnumImpl::Next](#next)|實作[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)。|  
|[CComEnumImpl::Reset](#reset)|實作[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)。|  
|[CComEnumImpl::Skip](#skip)|實作[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComEnumImpl::m_begin](#m_begin)|陣列中的第一個項目指標。|  
|[CComEnumImpl::m_dwFlags](#m_dwflags)|複製旗標傳遞`Init`。|  
|[CComEnumImpl::m_end](#m_end)|陣列中的最後一個項目之外的位置指標。|  
|[CComEnumImpl::m_iter](#m_iter)|陣列中目前項目的指標。|  
|[CComEnumImpl::m_spUnk](#m_spunk)|**IUnknown**提供列舉的集合物件的指標。|  
  
## <a name="remarks"></a>備註  
 `CComEnumImpl`提供列舉的項目儲存在陣列中的 COM 列舉程式介面的實作。 這個類別是類似於`IEnumOnSTLImpl`類別，可提供列舉值介面的實作，根據 c + + 標準程式庫容器。  
  
> [!NOTE]
>  如需有關進一步之間的差異`CComEnumImpl`和`IEnumOnSTLImpl`，請參閱[CComEnumImpl::Init](#init)。  
  
 一般而言，您將*不*必須建立您自己的列舉值類別衍生自這個介面的實作。 如果您想要使用陣列為基礎的 ATL 提供列舉值，比較常見建立的執行個體是[CComEnum](../../atl/reference/ccomenum-class.md)。  
  
 不過，如果您需要提供自訂的列舉值 （例如，一個公開除了列舉程式介面的介面），您可以從這個類別衍生。 在此情況下，很可能必須覆寫[CComEnumImpl::Clone](#clone)方法，以提供您自己的實作。  
  
 如需詳細資訊，請參閱[ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComEnumImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl  
 建構函式。  
  
```
CComEnumImpl();
```  
  
##  <a name="dtor"></a>CComEnumImpl:: ~ CComEnumImpl  
 解構函式。  
  
```
~CComEnumImpl();
```  
  
##  <a name="init"></a>CComEnumImpl::Init  
 您必須呼叫這個方法之前將指標傳遞給任何用戶端的列舉程式介面。  
  
```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```  
  
### <a name="parameters"></a>參數  
 *begin*  
 第一個項目，其中包含要列舉之項目的陣列的指標。  
  
 `end`  
 最後一個元素的陣列，包含要列舉的項目之外的位置指標。  
  
 *pUnk*  
 [in]**IUnknown**必須保持存留在生命週期的列舉值物件的指標。 傳遞**NULL**如果物件不存在。  
  
 `flags`  
 指定列舉值應該取得陣列的擁有權，或建立一份旗標。 以下是可能的值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 只有一次呼叫這個方法，初始化列舉值，請使用它，然後將它丟棄。  
  
 如果您將指標傳遞到保留在另一個物件的陣列中的項目 （而且您不要求將資料複製列舉值），您可以使用*pUnk*以確保物件和陣列，它會保留供只要列舉值需要這些參數。 列舉值只是要保持運作的物件持有 COM 參考。 終結列舉值時，就會自動釋放 COM 參考。  
  
 `flags`參數可讓您指定列舉值應該如何處理傳遞給它的陣列元素。 `flags`可能需要從值的其中一個**CComEnumFlags**列舉型別，如下所示︰  
  
```  
enum CComEnumFlags  
   {  
   AtlFlagNoCopy = 0,  
   AtlFlagTakeOwnership = 2, // BitOwn  
   AtlFlagCopy = 3           // BitOwn | BitCopy  
   };  
```  
  
 **AtlFlagNoCopy**表示陣列的存留期不會受到列舉值。 在此情況下，其中一個陣列會是靜態或所識別的物件*pUnk*負責在不再需要時釋放陣列。  
  
 **AtlFlagTakeOwnership**表示陣列的解構函式是列舉值所控制。 在此情況下，陣列必須以動態方式配置使用**新**。 列舉值將會刪除其解構函式中的陣列。 一般而言，您可以傳遞**NULL**的*pUnk*，不過您仍然可以傳遞有效的指標，如果您需要因故損毀的列舉值的通知。  
  
 **AtlFlagCopy**表示新的陣列，是要複製的陣列傳遞至建立`Init`。 新陣列的存留期為列舉值所控制。 列舉值將會刪除其解構函式中的陣列。 一般而言，您可以傳遞**NULL**的*pUnk*，不過您仍然可以傳遞有效的指標，如果您需要因故損毀的列舉值的通知。  
  
> [!NOTE]
>  這個方法的原型指定陣列元素為型別**T**，其中**T**定義為類別樣板參數。 這是相同的型別公開的 COM 介面方法透過[CComEnumImpl::Next](#next)。 這是，不同於[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)，這個類別不支援不同的儲存體和公開資料型別。 陣列中元素的資料型別必須是透過 COM 介面公開的資料類型相同。  
  
##  <a name="clone"></a>CComEnumImpl::Clone  
 這個方法提供實作[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)方法藉由建立型別的物件`CComEnum`，初始化具有相同的陣列和迭代器使用目前的物件，並傳回新建立的物件上的介面。  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]從目前的列舉值會複製新建立的物件上的列舉程式介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 請注意，複製的列舉值永遠不會讓他們自己使用原始的列舉值的資料複本 （或取得所有權 」）。 如有必要，複製的列舉值將保持原始的列舉值 （使用 COM 參考），只要在需要確保資料可供。  
  
##  <a name="m_spunk"></a>CComEnumImpl::m_spUnk  
 這個智慧型指標會維持物件傳遞至參考[CComEnumImpl::Init](#init)，確保它運作的列舉值的存留期間。  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
##  <a name="m_begin"></a>CComEnumImpl::m_begin  
 最後一個元素的陣列，包含要列舉的項目之外的位置指標。  
  
```
T* m_begin;
```  
  
##  <a name="m_end"></a>CComEnumImpl::m_end  
 第一個項目，其中包含要列舉之項目的陣列的指標。  
  
```
T* m_end;
```  
  
##  <a name="m_iter"></a>CComEnumImpl::m_iter  
 目前的項目，其中包含要列舉之項目的陣列的指標。  
  
```
T* m_iter;
```  
  
##  <a name="m_dwflags"></a>CComEnumImpl::m_dwFlags  
 旗標傳遞給[CComEnumImpl::Init](#init)。  
  
```
DWORD m_dwFlags;
```  
  
##  <a name="next"></a>CComEnumImpl::Next  
 這個方法提供實作[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)方法。  
  
```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
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
  
##  <a name="reset"></a>CComEnumImpl::Reset  
 這個方法提供實作[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)方法。  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="skip"></a>CComEnumImpl::Skip  
 這個方法提供實作[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)方法。  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>參數  
 `celt`  
 [in]略過的項目數目。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 如果傳回 E_INVALIDARG`celt`為零，傳回 S_FALSE，如果小於`celt`傳回項目，否則會傳回 S_OK。  
  
## <a name="see-also"></a>另請參閱  
 [IEnumOnSTLImpl 類別](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum 類別](../../atl/reference/ccomenum-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

