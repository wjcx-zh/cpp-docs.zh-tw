---
title: "CComClassFactorySingleton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComClassFactorySingleton
- ATL.CComClassFactorySingleton<T>
- ATL::CComClassFactorySingleton
- ATL::CComClassFactorySingleton<T>
- CComClassFactorySingleton
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
caps.latest.revision: 21
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
ms.openlocfilehash: 7ff6f3a9d00c0f579077d9502aefad5cbea35f17
ms.lasthandoff: 02/24/2017

---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton 類別
此類別衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別。  
  
 `CComClassFactorySingleton`衍生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，並使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)來建構單一物件。 每次呼叫`CreateInstance`方法只會查詢此物件的介面指標。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|查詢`m_spObj`的介面指標。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)所建構的物件`CComClassFactorySingleton`。|  
  
## <a name="remarks"></a>備註  
 ATL 物件通常取得一個 class factory，藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4)，它會宣告`CComClassFactory`作為預設類別處理站。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](http://msdn.microsoft.com/library/0e4a3964-c03d-463e-884c-fe3b416db478)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#10;](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-namecreateinstancea--ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CreateInstance  
 呼叫`QueryInterface`透過[m_spObj](#m_spobj)以擷取介面指標。  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>參數  
 `pUnkOuter`  
 [in]如果正在建立物件做為一部分的彙總，然後`pUnkOuter`必須是外部未知。 否則，`pUnkOuter`必須**NULL**。  
  
 `riid`  
 [in]所要求介面的 IID。 如果`pUnkOuter`是非**NULL**，`riid`必須**IID_IUnknown**。  
  
 `ppvObj`  
 [out]所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppvObj`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="a-namemspobja--ccomclassfactorysingletonmspobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj  
 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)所建構的物件`CComClassFactorySingleton`。  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>備註  
 每次呼叫[CreateInstance](#createinstance)方法只會查詢此物件的介面指標。  
  
 請注意，目前的表單`m_spObj`顯示重大變更的方式，`CComClassFactorySingleton`曾在舊版的 ATL 在舊版`CComClassFactorySingleton`作為類別處理站，同時在伺服器初始化期間建立物件。 Visual c + +.NET 2003年中建立物件時，延遲的第一個要求。 這項變更可能導致早期初始化所依賴的程式中的錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)

