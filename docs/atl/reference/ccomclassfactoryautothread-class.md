---
title: CComClassFactoryAutoThread 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbd258761bef7789e73fe61ac288b414902d2af8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214070"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread 類別
這個類別會實作[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)介面，並允許在多個 apartment 中建立的物件。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|建立指定的 CLSID 的物件。|  
|[CComClassFactoryAutoThread::LockServer](#lockserver)|鎖定記憶體中的 class factory。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactoryAutoThread` 類似於[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允許在多個 apartment 中建立的物件。 若要利用這項支援，衍生您的 EXE 模組，從[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactoryAutoThread::CreateInstance  
 建立指定的 CLSID 的物件，並擷取此物件的介面指標。  
  
```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>參數  
 *pUnkOuter*  
 [in]如果物件過程中建立的彙總，然後*pUnkOuter*必須是外部未知。 否則，請*pUnkOuter*必須是 NULL。  
  
 *riid*  
 [in]要求的介面 IID。 如果*pUnkOuter*為非 NULL *riid*必須是`IID_IUnknown`。  
  
 *ppvObj*  
 [out]所識別之介面指標的指標*riid*。 如果物件不支援這個介面， *ppvObj*設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 如果您的模組是衍生自[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，`CreateInstance`第一次選取執行緒相關聯的 apartment 中建立物件。  
  
##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer  
 遞增和遞減模組鎖定計數藉由呼叫`_Module::Lock`和`_Module::Unlock`分別。  
  
```
STDMETHODIMP LockServer(BOOL fLock);
```  
  
### <a name="parameters"></a>參數  
 *fLock*  
 [in]如果為 TRUE，就會遞增的鎖定計數;否則，鎖定計數會遞減。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 使用時`CComClassFactoryAutoThread`，`_Module`通常是指全域執行個體[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 呼叫`LockServer`允許用戶端，以便可以快速建立多個物件保留的 class factory。  
  
## <a name="see-also"></a>另請參閱  
 [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)   
 [CComClassFactory2 類別](../../atl/reference/ccomclassfactory2-class.md)   
 [CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)
