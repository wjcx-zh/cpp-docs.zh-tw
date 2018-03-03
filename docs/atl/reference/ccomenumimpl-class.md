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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cda4598f5d5b0e5b3dbca265066c8366cfd6d67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|建構函式。|  
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComEnumImpl::Clone](#clone)|實作[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)。|  
|[CComEnumImpl::Init](#init)|初始化列舉值。|  
|[CComEnumImpl::Next](#next)|實作[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)。|  
|[CComEnumImpl::Reset](#reset)|實作[IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx)。|  
|[CComEnumImpl::Skip](#skip)|實作[IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx)。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComEnumImpl::m_begin](#m_begin)|陣列中的第一個項目指標。|  
|[CComEnumImpl::m_dwFlags](#m_dwflags)|複製旗標傳遞`Init`。|  
|[CComEnumImpl::m_end](#m_end)|陣列中的最後一個項目之外的位置指標。|  
|[CComEnumImpl::m_iter](#m_iter)|陣列中目前的項目指標。|  
|[CComEnumImpl::m_spUnk](#m_spunk)|**IUnknown**提供列舉的集合物件的指標。|  
  
## <a name="remarks"></a>備註  
 `CComEnumImpl`提供列舉的項目儲存在陣列中的 COM 列舉程式介面的實作。 這個類別是類似於`IEnumOnSTLImpl`類別，可提供列舉值介面的實作，根據 c + + 標準程式庫容器。  
  
> [!NOTE]
>  如需詳細資訊，進一步之間的差異`CComEnumImpl`和`IEnumOnSTLImpl`，請參閱[CComEnumImpl::Init](#init)。  
  
 一般而言，您將*不*必須建立您自己的列舉值類別衍生自這個介面實作。 如果您想要使用 ATL 提供列舉值的陣列為基礎，它是建立的執行個體更常見[CComEnum](../../atl/reference/ccomenum-class.md)。  
  
 不過，如果您需要提供自訂的列舉值 （例如，一個公開除了列舉程式介面的介面），您可以從這個類別衍生。 在此情況下，可能是，您必須覆寫[CComEnumImpl::Clone](#clone)方法以提供您自己的實作。  
  
 如需詳細資訊，請參閱[ATL 集合和列舉程式](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Base`  
  
 `CComEnumImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
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
 您必須將指標傳遞給列舉值介面傳回給任何用戶端之前呼叫這個方法。  
  
```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```  
  
### <a name="parameters"></a>參數  
 *begin*  
 第一個項目，包含要列舉之項目的陣列的指標。  
  
 `end`  
 包含要列舉之項目的陣列的最後一個項目之外的位置指標。  
  
 *pUnk*  
 [in]**IUnknown**指標必須保持運作的列舉值的存留期間的物件。 傳遞**NULL**如果物件不存在。  
  
 `flags`  
 指定列舉值應該取得陣列的擁有權，或建立一份旗標。 以下將說明可能的值。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 只能呼叫一次這個方法，初始化列舉值，請使用它，然後將它丟棄。  
  
 如果您將指標傳遞至保存在另一個物件的陣列中的項目 （而且您不要詢問要複製資料的列舉值），您可以使用*pUnk*參數，以確保物件和陣列保留的可用只要列舉值需要它們。 列舉值只會保留要保持運作的物件上的 COM 參考。 終結列舉值時，就會自動釋放 COM 參考。  
  
 `flags`參數可讓您指定列舉值應該如何處理陣列項目傳遞給它。 `flags`可能需要其中一個值從**CComEnumFlags**列舉型別，如下所示：  
  
```  
enum CComEnumFlags  
   {  
   AtlFlagNoCopy = 0,  
   AtlFlagTakeOwnership = 2, // BitOwn  
   AtlFlagCopy = 3           // BitOwn | BitCopy  
   };  
```  
  
 **AtlFlagNoCopy**表示陣列的存留期不受列舉值。 在此情況下，其中一個陣列會是靜態或所識別的物件*pUnk*將負責在不再需要時釋放陣列。  
  
 **AtlFlagTakeOwnership**表示損毀的陣列是列舉值所控制。 在此情況下，陣列必須以動態方式配置使用**新**。 列舉值將會刪除其解構函式中的陣列。 一般而言，您可以傳遞**NULL**如*pUnk*，不過您仍然可以傳遞有效的指標，如果您需要因故損毀的列舉值的通知。  
  
 **AtlFlagCopy**表示新的陣列，是要複製的陣列傳遞至建立`Init`。 新陣列的存留期為列舉值所控制。 列舉值將會刪除其解構函式中的陣列。 一般而言，您可以傳遞**NULL**如*pUnk*，不過您仍然可以傳遞有效的指標，如果您需要因故損毀的列舉值的通知。  
  
> [!NOTE]
>  這個方法的原型為型別指定陣列項目**T**，其中**T**定義為類別樣板參數。 這是公開透過 COM 介面方法的相同類型[CComEnumImpl::Next](#next)。 含意是，不同於[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)，這個類別不支援不同的儲存體和公開資料型別。 陣列中元素的資料類型必須是透過 COM 介面公開的資料類型相同。  
  
##  <a name="clone"></a>CComEnumImpl::Clone  
 這個方法提供實作[IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx)方法藉由建立型別的物件`CComEnum`，初始化具有相同的陣列與目前物件所使用的迭代器，並在傳回介面新建立的物件。  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>參數  
 `ppEnum`  
 [out]從目前的列舉值，複製新建立的物件上的列舉程式介面。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 請注意，複製的列舉值永遠不會讓他們自己使用原始的列舉值的資料複本 （或 take ownership）。 如有必要，複製的列舉值會保留原始的列舉值運作 （使用 COM 參考） 來確保資料是供，只要在需要。  
  
##  <a name="m_spunk"></a>CComEnumImpl::m_spUnk  
 這個智慧型指標會維持對傳遞至的物件參考[CComEnumImpl::Init](#init)，確保保持運作的列舉值的存留期間。  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
##  <a name="m_begin"></a>CComEnumImpl::m_begin  
 包含要列舉之項目的陣列的最後一個項目之外的位置指標。  
  
```
T* m_begin;
```  
  
##  <a name="m_end"></a>CComEnumImpl::m_end  
 第一個項目，包含要列舉之項目的陣列的指標。  
  
```
T* m_end;
```  
  
##  <a name="m_iter"></a>CComEnumImpl::m_iter  
 目前的項目，包含要列舉之項目的陣列的指標。  
  
```
T* m_iter;
```  
  
##  <a name="m_dwflags"></a>CComEnumImpl::m_dwFlags  
 旗標傳遞至[CComEnumImpl::Init](#init)。  
  
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
 [in]要求的元素數目。  
  
 `rgelt`  
 [out]要填入之項目的陣列。  
  
 `pceltFetched`  
 [out]中實際傳回的項目數目`rgelt`。 這可以是小於`celt`如果少於`celt`保持在清單中的項目。  
  
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
 如果 `celt` 為0，則返回E_INVALIDARG，如果返回少於 `celt` 個元素則返回S_FALSE，否則返回S_OK。  
  
## <a name="see-also"></a>請參閱  
 [IEnumOnSTLImpl 類別](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum 類別](../../atl/reference/ccomenum-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
