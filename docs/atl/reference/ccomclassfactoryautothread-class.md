---
title: "CComClassFactoryAutoThread 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComClassFactoryAutoThread
- ATL.CComClassFactoryAutoThread
- CComClassFactoryAutoThread
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: fcc5671fc136b061bf3e8109999ac91d302d3d3b
ms.lasthandoff: 02/24/2017

---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread 類別
這個類別會實作[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)介面，並讓您在多個 apartment 中建立的物件。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|建立指定 CLSID 的物件。|  
|[CComClassFactoryAutoThread::LockServer](#lockserver)|鎖定記憶體中的 class factory。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactoryAutoThread`類似於[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但可在多個 apartment 中建立的物件。 若要利用這項支援，衍生您的 EXE 模組從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 ATL 物件通常取得一個 class factory，藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4)，它會宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作為預設類別處理站。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#9;](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-namecreateinstancea--ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance  
 建立指定 CLSID 的物件，並擷取這個物件的介面指標。  
  
```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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
  
### <a name="remarks"></a>備註  
 如果您的模組衍生自[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，`CreateInstance`會先選取相關聯的 apartment 中建立物件的執行緒。  
  
##  <a name="a-namelockservera--ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComClassFactoryAutoThread::LockServer  
 遞增和遞減模組鎖定計數藉由呼叫**_Module::Lock**和**_Module::Unlock**分別。  
  
```
STDMETHODIMP LockServer(BOOL fLock);
```  
  
### <a name="parameters"></a>參數  
 `fLock`  
 [in]如果**TRUE**的鎖定計數遞增; 否則鎖定計數會遞減。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 當使用`CComClassFactoryAutoThread`， **_Module**通常是指全域執行個體[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 呼叫`LockServer`允許用戶端保留一個 class factory，以便可以快速建立多個物件。  
  
## <a name="see-also"></a>另請參閱  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)

