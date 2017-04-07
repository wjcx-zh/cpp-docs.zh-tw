---
title: "IDispEventImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: 22
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 235955f8573ae7e430be3de2a96efdd7496d15de
ms.lasthandoff: 02/24/2017

---
# <a name="idispeventimpl-class"></a>IDispEventImpl 類別
這個類別提供的實作`IDispatch`方法。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```  
  
#### <a name="parameters"></a>參數  
 `nID`  
 來源物件的唯一識別項。 當`IDispEventImpl`是基底類別對於複合控制項，內含的控制項所需的資源識別碼，將這個參數。 在其他情況下，使用任意的正整數值。  
  
 `T`  
 使用者的類別，衍生自`IDispEventImpl`。  
  
 `pdiid`  
 這個類別所實作的事件分配介面的 IID 指標。 此介面必須定義在所表示的型別程式庫`plibid`， `wMajor`，和`wMinor`。  
  
 `plibid`  
 定義分派介面的類型程式庫指標所指`pdiid`。 如果**i GUID_NULL**，將會從來源之事件的物件來載入型別程式庫。  
  
 `wMajor`  
 型別程式庫的主要版本。 預設值為 0。  
  
 `wMinor`  
 次要類型程式庫版本。 預設值為 0。  
  
 `tihclass`  
 用來管理的型別資訊的類別`T`。 預設值是一種型別`CComTypeInfoHolder`; 不過，您可以藉由提供型別的類別以外的其他覆寫此範本參數`CComTypeInfoHolder`。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用來管理的型別資訊的類別。 根據預設， `CComTypeInfoHolder`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|找出指定的分派識別項的函式索引。|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|將單一成員和一組選擇性的引數名稱對應至相對應的 Dispid 的整數。|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|擷取物件的型別資訊。|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|擷取類型資訊介面數目。|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|擷取使用者定義型別的基本類型。|  
  
## <a name="remarks"></a>備註  
 `IDispEventImpl`提供一種實作事件分配程式介面，而不需要您提供每個方法/事件介面的實作程式碼。 `IDispEventImpl`提供的實作`IDispatch`方法。 您只需要提供您所需處理事件的實作。  
  
 `IDispEventImpl`可搭配[事件接收對應](http://msdn.microsoft.com/library/32542b3d-ac43-4139-8ac4-41c48481744f)路由至適當的處理常式函式的事件類別中。 若要使用這個類別︰  
  

 新增[SINK_ENTRY](http://msdn.microsoft.com/library/33a5fff6-5248-47c0-8cf4-8bdf760e86e5)或[SINK_ENTRY_EX](http://msdn.microsoft.com/library/e1d14342-838f-4791-ac2f-5dae2801c1ac)巨集，以您想要處理每個物件上的每個事件的事件接收對應。 當使用`IDispEventImpl`複合控制項的基底類別，您可以呼叫[AtlAdviseSinkMap](http://msdn.microsoft.com/library/0757a6af-3de3-4179-8b4f-ccd137d919b4)來建立與中斷連線，事件來源的所有項目會在事件接收對應。 在其他情況下，或取得更佳控制，呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)之間建立連線的來源物件和基底類別。 呼叫[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)中斷連線。  

  
 您必須衍生自`IDispEventImpl`(使用的唯一值`nID`) 針對每個您要處理事件的物件。 可以對一個來源物件針對不同的來源物件，然後通知取消通知重複使用的基底類別，但可以一次處理單一物件的來源物件的數目上限受限於數目`IDispEventImpl`基底類別。  
  
 `IDispEventImpl`提供相同的功能[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，但它會從類型程式庫，而不需要它提供的指標取得介面的型別資訊[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構。 使用`IDispEventSimpleImpl`當您沒有可以描述事件介面的型別程式庫或想要避免使用型別程式庫相關聯的額外負荷。  
  
> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供自己的實作**Iid**啟用每個`IDispEventImpl`和`IDispEventSimpleImpl`基底類別做為個別的 COM 身分識別，同時仍允許對類別成員的直接存取主要的 COM 物件中。  
  
 CE ATL 實作 ActiveX 事件接收唯一支援的傳回值型別 HRESULT 或 void 從您的事件處理常式方法。任何傳回的值不受支援，且其行為未定義。  
  
 如需詳細資訊，請參閱[支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId  
 找出指定的分派識別項的函式索引。  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>參數  
 `iid`  
 [in]參考的函式 ID。  
  
 *dispidMember*  
 [in]函式的分派 ID。  
  
 `lcid`  
 [in]地區設定內容的函式 id。  
  
 `info`  
 [in]結構，表示呼叫的函式的方式。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames  
 單一成員和一組選擇性的引數名稱對應至一組對應的整數 Dispid，可以用在後續呼叫[Excepinfo](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo  
 擷取物件的類型資訊，可以用來取得介面的類型資訊。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount  
 擷取物件提供的類型資訊介面數目 (0 或 1)。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType  
 擷取使用者定義型別的基本類型。  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>參數  
 `pTI`  
 [in]指標[ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680)介面包含使用者定義型別。  
  
 *hrt*  
 [in]要擷取之型別描述控制代碼。  
  
### <a name="return-value"></a>傳回值  
 Variant 型別。  
  
### <a name="remarks"></a>備註  
 請參閱[ITypeInfo::GetRefTypeInfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00)。  
  
##  <a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl  
 建構函式。 儲存類別樣板參數的值`plibid`， `pdiid`， `wMajor`，和`wMinor`。  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>IDispEventImpl::tihclass  
 此 typedef 是類別樣板參數的執行個體`tihclass`。  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>備註  
 根據預設，類別是`CComTypeInfoHolder`。 `CComTypeInfoHolder`管理類別的型別資訊。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](http://msdn.microsoft.com/library/33a5fff6-5248-47c0-8cf4-8bdf760e86e5)   
 [SINK_ENTRY_EX](http://msdn.microsoft.com/library/e1d14342-838f-4791-ac2f-5dae2801c1ac)   
 [SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)   
 [類別概觀](../../atl/atl-class-overview.md)
