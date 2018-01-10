---
title: "CComClassFactory2 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5b1626a9ce7ef729416f7e6e1a6d3c60836dbed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 實作下列靜態函式的類別：  
  
- **靜態 BOOL VerifyLicenseKey (BSTR** `bstr` **);**  
  
- **靜態 BOOL GetLicenseKey (DWORD** `dwReserved` **，BSTR\***  `pBstr` **);**  
  
- **靜態 BOOL IsLicenseValid （);**  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|建立指定的 CLSID 的物件。|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|指定的授權金鑰，建立指定的 CLSID 的物件。|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|擷取說明的 class factory 的授權功能的資訊。|  
|[CComClassFactory2::LockServer](#lockserver)|鎖定在記憶體中的 class factory。|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|建立並傳回授權金鑰。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactory2`實作[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)介面的擴充功能的[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)。 **IClassFactory2**控制項物件透過授權建立。 類別處理站執行授權的電腦上，可以提供執行階段授權金鑰。 這個授權金鑰可讓應用程式的完整電腦授權不存在時，將物件具現化。  
  
 ATL 物件通常由衍生自取得 class factory [CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**，在樣板參數`CComClassFactory2`，必須實作的靜態函式`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 以下是簡單的授權類別的範例：  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2`衍生自兩者**CComClassFactory2Base**和*授權*。 **CComClassFactory2Base**，又，衍生自**IClassFactory2**和**CComObjectRootEx\< CComGlobalsThreadModel >**。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactory2::CreateInstance  
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
  
### <a name="remarks"></a>備註  
 需要完整授權。 完整的電腦授權不存在，如果呼叫[CreateInstanceLic](#createinstancelic)。  
  
##  <a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic  
 類似於[CreateInstance](#createinstance)，不同之處在於`CreateInstanceLic`需要授權金鑰。  
  
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
 [in]如果物件建立為彙總時，部分然後`pUnkOuter`必須是外部未知。 否則，`pUnkOuter`必須**NULL**。  
  
 *pUnkReserved*  
 [in]未使用。 必須是**NULL**。  
  
 `riid`  
 [in]所要求介面的 IID。 如果`pUnkOuter`是非**NULL**，`riid`必須**IID_IUnknown**。  
  
 `bstrKey`  
 [in]執行階段授權金鑰之前取得呼叫`RequestLicKey`。 這個索引鍵，才能建立物件。  
  
 `ppvObject`  
 [out]所指定的介面指標的指標`riid`。 如果物件不支援這個介面，`ppvObject`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 您可以取得授權金鑰使用[RequestLicKey](#requestlickey)。 若要在未經授權的電腦上建立物件，您必須呼叫`CreateInstanceLic`。  
  
##  <a name="getlicinfo"></a>CComClassFactory2::GetLicInfo  
 填滿[LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590)結構描述的 class factory 的資訊的授權功能。  
  
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
 [in]如果**TRUE**、 鎖定計數遞增; 否則鎖定計數會遞減。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 **_Module**的全域執行個體是指[CComModule](../../atl/reference/ccommodule-class.md)或從其衍生的類別。  
  
 呼叫`LockServer`允許用戶端保留 class factory，以便可以快速地建立多個物件。  
  
##  <a name="requestlickey"></a>CComClassFactory2::RequestLicKey  
 建立並傳回授權金鑰，但前提是`fRuntimeKeyAvail`隸屬[LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590)結構是**TRUE**。  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>參數  
 `dwReserved`  
 [in]未使用。 必須是零。  
  
 `pbstrKey`  
 [out]指標的授權金鑰。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 授權金鑰所呼叫的[CreateInstanceLic](#createinstancelic)未經授權的電腦上建立的物件。 如果`fRuntimeKeyAvail`是**FALSE**，則物件只會建立完整授權的電腦上。  
  
 呼叫[GetLicInfo](#getlicinfo)擷取的值`fRuntimeKeyAvail`。  
  
## <a name="see-also"></a>請參閱  
 [CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)
