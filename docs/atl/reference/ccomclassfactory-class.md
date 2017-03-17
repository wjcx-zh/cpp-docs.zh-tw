---
title: "CComClassFactory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c7c488732d7b32248acaaa5c5c9c6a29404c3872
ms.lasthandoff: 02/24/2017

---
# <a name="ccomclassfactory-class"></a>CComClassFactory 類別
這個類別會實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面。  
  
## <a name="syntax"></a>語法  
  
```
class CComClassFactory 
   : public IClassFactory,  
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](#createinstance)|建立指定 CLSID 的物件。|  
|[CComClassFactory::LockServer](#lockserver)|鎖定記憶體中的 class factory。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactory`實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面，其中包含用於建立特定的 CLSID、 的物件，以及鎖定在記憶體中允許更快速地建立新物件的 class factory 方法。 **IClassFactory**必須針對您在系統登錄中，與您指定 CLSID 註冊每個類別中實作。  
  
 ATL 物件通常取得一個 class factory，藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4)，它會宣告`CComClassFactory`作為預設類別處理站。 若要覆寫這個預設值，指定的其中一個`DECLARE_CLASSFACTORY` *XXX*類別定義中的巨集。 例如， [DECLARE_CLASSFACTORY_EX](http://msdn.microsoft.com/library/4181ef00-0f30-4e19-b0ee-e7648062e926)巨集的 class factory 會使用指定的類別︰  
  
 [!code-cpp[NVC_ATL_COM&#8;](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 上述類別定義中指定**CMyClassFactory**當做物件的預設類別處理站。 **CMyClassFactory**必須衍生自`CComClassFactory`並覆寫`CreateInstance`。  
  
 ATL 提供三個宣告的類別處理站的其他巨集︰  
  
- [DECLARE_CLASSFACTORY2](http://msdn.microsoft.com/library/38a6c969-7297-4bb1-9ba6-1fe2d355b285)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，哪些控制項透過授權建立。  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，這會在多個 apartment 中建立物件。  
  
- [DECLARE_CLASSFACTORY_SINGLETON](http://msdn.microsoft.com/library/0e4a3964-c03d-463e-884c-fe3b416db478)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，這會建構一個[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactory::CreateInstance  
 建立指定 CLSID 的物件，並擷取這個物件的介面指標。  
  
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
  
##  <a name="lockserver"></a>CComClassFactory::LockServer  
 遞增和遞減模組鎖定計數藉由呼叫**_Module::Lock**和**_Module::Unlock**分別。  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>參數  
 `fLock`  
 [in]如果**TRUE**的鎖定計數遞增; 否則鎖定計數會遞減。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 **_Module**參考的全域執行個體的[CComModule](../../atl/reference/ccommodule-class.md)或從中衍生的類別。  
  
 呼叫`LockServer`允許用戶端保留一個 class factory，以便可以快速建立多個物件。  
  
## <a name="see-also"></a>另請參閱  
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)

