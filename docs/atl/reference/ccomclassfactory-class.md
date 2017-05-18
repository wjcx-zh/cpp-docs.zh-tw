---
title: "CComClassFactory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: a0c1c115bfffa1de9a2a8c91c5268de66c68e7cd
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

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
|[CComClassFactory::CreateInstance](#createinstance)|建立指定的 CLSID 的物件。|  
|[CComClassFactory::LockServer](#lockserver)|鎖定在記憶體中的 class factory。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactory`實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面，其中包含用於建立特定的 CLSID 的物件，以及鎖定以允許更快速地建立新物件的記憶體中的 class factory 方法。 **IClassFactory**必須針對您在系統登錄中，並為您指派為 CLSID 註冊每個類別中實作。  
  
 ATL 物件通常由衍生自取得 class factory [CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中宣告`CComClassFactory`做為預設 class factory。 若要覆寫此預設值，指定的其中一個`DECLARE_CLASSFACTORY` *XXX*類別定義中的巨集。 例如， [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex)巨集的 class factory 中用於指定的類別︰  
  
 [!code-cpp[NVC_ATL_COM #8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 上述類別定義指定**CMyClassFactory**將使用做為物件的預設 class factory。 **CMyClassFactory**必須衍生自`CComClassFactory`並覆寫`CreateInstance`。  
  
 ATL 提供三個其他宣告 class factory 的巨集︰  
  
- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，這會控制透過授權建立。  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，這會在多個 apartment 中建立物件。  
  
- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，這會建構一個[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactory::CreateInstance  
 建立指定的 CLSID 的物件，並擷取這個物件的介面指標。  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>參數  
 `pUnkOuter`  
 [in]如果物件建立為彙總時，部分然後`pUnkOuter`必須是外部未知。 否則，`pUnkOuter`必須**NULL**。  
  
 `riid`  
 [in]所要求介面的 IID。 如果`pUnkOuter`是非**NULL**，`riid`必須**IID_IUnknown**。  
  
 `ppvObj`  
 [out]所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppvObj`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="lockserver"></a>CComClassFactory::LockServer  
 遞增和遞減模組鎖定計數藉由呼叫**_Module::Lock**和**_Module::Unlock**分別。  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>參數  
 `fLock`  
 [in]如果**TRUE**、 鎖定計數遞增; 否則鎖定計數會遞減。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 **_Module**的全域執行個體是指[CComModule](../../atl/reference/ccommodule-class.md)或從其衍生的類別。  
  
 呼叫`LockServer`允許用戶端保留 class factory，以便可以快速地建立多個物件。  
  
## <a name="see-also"></a>另請參閱  
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)

