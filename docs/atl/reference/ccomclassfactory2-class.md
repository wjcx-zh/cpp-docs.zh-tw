---
title: "CComClassFactory2 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
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
ms.openlocfilehash: 3787214d5479e1cd57295c9c25335e87651a16bb
ms.lasthandoff: 02/24/2017

---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 類別
這個類別會實作[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)介面。  
  
## <a name="syntax"></a>語法  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>參數  
 *授權*  
 類別會實作下列靜態函式︰  
  
- **靜態 BOOL VerifyLicenseKey (BSTR** `bstr` **);**  
  
- **靜態 BOOL GetLicenseKey (DWORD** `dwReserved` **，BSTR\* ** `pBstr` **);**  
  
- **靜態 BOOL IsLicenseValid （);**  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|建立指定 CLSID 的物件。|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|指定的授權金鑰，會建立指定 CLSID 的物件。|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|擷取的 class factory 的授權功能的說明資訊。|  
|[CComClassFactory2::LockServer](#lockserver)|鎖定記憶體中的 class factory。|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|建立並傳回授權金鑰。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactory2`實作[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)介面的擴充功能的[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)。 **IClassFactory2**控制項物件建立到授權。 類別處理站執行授權的電腦上，可以提供執行階段授權金鑰。 這種授權金鑰可讓應用程式的完整電腦授權不存在時，具現化物件。  
  
 ATL 物件通常取得一個 class factory，藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](http://msdn.microsoft.com/library/51a6b925-07c0-4d3a-9174-0b8c808975e4)，它會宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作為預設類別處理站。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](http://msdn.microsoft.com/library/38a6c969-7297-4bb1-9ba6-1fe2d355b285)物件的類別定義中的巨集。 例如：  
  
 [!code-cpp[NVC_ATL_COM&#2;](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**，樣板參數`CComClassFactory2`，必須實作的靜態函式`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 以下是簡單的授權類別的範例︰  
  
 [!code-cpp[NVC_ATL_COM&#3;](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2`衍生自兩者**CComClassFactory2Base**和*授權*。 **CComClassFactory2Base**，反而是衍生自**IClassFactory2**和**CComObjectRootEx\< CComGlobalsThreadModel >**。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactory2::CreateInstance  
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
  
### <a name="remarks"></a>備註  
 需要完整授權的電腦。 完整電腦授權不存在，如果呼叫[CreateInstanceLic](#createinstancelic)。  
  
##  <a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic  
 類似於[CreateInstance](#createinstance)，只不過`CreateInstanceLic`需要授權金鑰。  
  
```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
 */,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```  
  
### <a name="parameters"></a>參數  
 `pUnkOuter`  
 [in]如果正在建立物件做為一部分的彙總，然後`pUnkOuter`必須是外部未知。 否則，`pUnkOuter`必須**NULL**。  
  
 *pUnkReserved*  
 [in]未使用。 必須是**NULL**。  
  
 `riid`  
 [in]所要求介面的 IID。 如果`pUnkOuter`是非**NULL**，`riid`必須**IID_IUnknown**。  
  
 `bstrKey`  
 [in]執行階段授權金鑰之前取得呼叫`RequestLicKey`。 需要此金鑰來建立物件。  
  
 `ppvObject`  
 [out]所指定的介面指標的指標`riid`。 如果物件不支援這個介面，`ppvObject`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 您可以取得授權金鑰使用[RequestLicKey](#requestlickey)。 為了在未經授權的電腦上建立物件，您必須呼叫`CreateInstanceLic`。  
  
##  <a name="getlicinfo"></a>CComClassFactory2::GetLicInfo  
 填滿[LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590)結構描述的 class factory 資訊的授權功能。  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>參數  
 *pLicInfo*  
 [out]指標**LICINFO**結構。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 `fRuntimeKeyAvail`這個結構的成員表示是否提供授權金鑰，class factory 允許未經授權的電腦上建立的物件。 *FLicVerified*成員表示的完整電腦授權是否存在。  
  
##  <a name="lockserver"></a>CComClassFactory2::LockServer  
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
  
##  <a name="requestlickey"></a>CComClassFactory2::RequestLicKey  
 建立並傳回授權金鑰，但前提是`fRuntimeKeyAvail`成員[LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590)結構是**TRUE**。  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>參數  
 `dwReserved`  
 [in]未使用。 必須為零。  
  
 `pbstrKey`  
 [out]授權金鑰的指標。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 授權金鑰，呼叫才[CreateInstanceLic](#createinstancelic)未經授權的電腦上建立的物件。 如果`fRuntimeKeyAvail`是**FALSE**，則只有在完整授權版的電腦上建立物件。  
  
 呼叫[GetLicInfo](#getlicinfo)來擷取值`fRuntimeKeyAvail`。  
  
## <a name="see-also"></a>另請參閱  
 [CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)

