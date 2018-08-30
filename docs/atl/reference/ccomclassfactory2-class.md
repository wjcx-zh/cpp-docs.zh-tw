---
title: CComClassFactory2 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe4ddaab8de2369c7cb1b31132f686bc6037676b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205521"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 類別
這個類別會實作[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)介面。  
  
## <a name="syntax"></a>語法  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>參數  
 *授權*  
 類別若實作下列靜態函式：  
  
- `static BOOL VerifyLicenseKey( BSTR bstr );`  
  
- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`  
  
- `static BOOL IsLicenseValid( );`  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|建立指定的 CLSID 的物件。|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|指定的授權金鑰，會建立指定的 CLSID 的物件。|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|擷取描述的 class factory 的授權功能的資訊。|  
|[CComClassFactory2::LockServer](#lockserver)|鎖定記憶體中的 class factory。|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|建立並傳回的授權金鑰。|  
  
## <a name="remarks"></a>備註  
 `CComClassFactory2` 會實作[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)介面，這是延伸模組的[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)。 `IClassFactory2` 透過授權的控制項物件建立。 類別處理站執行已授權的電腦上，可以提供執行階段授權金鑰。 這種授權金鑰可讓應用程式的完整機器授權不存在時，具現化物件。  
  
 ATL 物件通常取得 class factory 藉由衍生自[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 這個類別包含巨集[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)，其中宣告[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)做為預設 class factory。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)物件的類別定義中的巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 `CMyLicense`要與範本參數`CComClassFactory2`，必須實作的靜態函式`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 以下是簡單的授權類別的範例：  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` 衍生自兩者`CComClassFactory2Base`並*授權*。 `CComClassFactory2Base`反而是衍生自`IClassFactory2`和`CComObjectRootEx< CComGlobalsThreadModel >`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance  
 建立指定的 CLSID 的物件，並擷取此物件的介面指標。  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
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
 需要電腦的完整授權。 如果不存在完整的機器授權，呼叫[CreateInstanceLic](#createinstancelic)。  
  
##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic  
 類似於[CreateInstance](#createinstance)，差異在於`CreateInstanceLic`需要的授權金鑰。  
  
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
 *pUnkOuter*  
 [in]如果物件過程中建立的彙總，然後*pUnkOuter*必須是外部未知。 否則，請*pUnkOuter*必須是 NULL。  
  
 *pUnkReserved*  
 [in]不使用。 必須是 NULL。  
  
 *riid*  
 [in]要求的介面 IID。 如果*pUnkOuter*為非 NULL *riid*必須是`IID_IUnknown`。  
  
 *bstrKey*  
 [in]執行階段授權金鑰之前取得呼叫`RequestLicKey`。 此金鑰，才能建立物件。  
  
 *ppvObject*  
 [out]所指定的介面指標的指標*riid*。 如果物件不支援這個介面， *ppvObject*設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 您可以取得授權金鑰 using [RequestLicKey](#requestlickey)。 若要建立物件，在未經授權的電腦上，您必須呼叫`CreateInstanceLic`。  
  
##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo  
 填滿[LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo)結構描述的 class factory 資訊的授權功能。  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>參數  
 *pLicInfo*  
 [out]指標`LICINFO`結構。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 `fRuntimeKeyAvail`這個結構的成員會指出是否，取得授權金鑰，class factory 允許未經授權的電腦上建立的物件。 *FLicVerified*成員表示完整的電腦授權是否存在。  
  
##  <a name="lockserver"></a>  CComClassFactory2::LockServer  
 遞增和遞減模組鎖定計數藉由呼叫`_Module::Lock`和`_Module::Unlock`分別。  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>參數  
 *fLock*  
 [in]如果為 TRUE，就會遞增的鎖定計數;否則，鎖定計數會遞減。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 `_Module` 全域執行個體是指[CComModule](../../atl/reference/ccommodule-class.md)或從它衍生的類別。  
  
 呼叫`LockServer`允許用戶端，以便可以快速建立多個物件保留的 class factory。  
  
##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey  
 建立並傳回授權金鑰，但前提`fRuntimeKeyAvail`隸屬[LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo)結構為 TRUE。  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>參數  
 *dwReserved*  
 [in]不使用。 必須是零。  
  
 *pbstrKey*  
 [out]授權金鑰的指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 呼叫的授權金鑰須[CreateInstanceLic](#createinstancelic)未經授權的電腦上建立的物件。 如果`fRuntimeKeyAvail`是 FALSE，則只有在完整授權版的電腦上建立物件。  
  
 呼叫[GetLicInfo](#getlicinfo)擷取的值`fRuntimeKeyAvail`。  
  
## <a name="see-also"></a>另請參閱  
 [CComClassFactoryAutoThread 類別](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton 類別](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [類別概觀](../../atl/atl-class-overview.md)
