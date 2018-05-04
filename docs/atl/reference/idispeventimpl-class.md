---
title: IDispEventImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7809a61fe39a4b4b913531de29e03c3eb440c418
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 類別
這個類別提供的實作`IDispatch`方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
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
 來源物件的唯一識別碼。 當`IDispEventImpl`的基底類別的複合控制項，使用此參數包含所需的控制項的資源識別碼。 在其他情況下，使用任意的正整數。  
  
 `T`  
 使用者的類別，衍生自`IDispEventImpl`。  
  
 `pdiid`  
 這個類別所實作的事件分配程式介面的 IID 指標。 此介面必須定義在所表示的類型程式庫`plibid`， `wMajor`，和`wMinor`。  
  
 `plibid`  
 類型程式庫定義分派介面的指標所指向`pdiid`。 如果 **& GUID_NULL**，將會從來源之事件的物件來載入類型程式庫。  
  
 `wMajor`  
 類型程式庫的主要版本。 預設值為 0。  
  
 `wMinor`  
 類型程式庫的次要版本。 預設值為 0。  
  
 `tihclass`  
 用來管理的類型資訊的類別`T`。 預設值是類型的類別之`CComTypeInfoHolder`; 不過，您可以藉由提供的型別類別不覆寫此範本參數`CComTypeInfoHolder`。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用來管理的類型資訊的類別。 根據預設， `CComTypeInfoHolder`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|找出指定的分派識別項的函式索引。|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|將單一成員和一組選擇性的引數名稱對應至相對應的 Dispid 的整數。|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|擷取物件的類型資訊。|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|擷取類型資訊介面數目。|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|擷取使用者自訂類型的基本類型。|  
  
## <a name="remarks"></a>備註  
 `IDispEventImpl` 提供一種實作的事件分配程式介面，而不需要您提供每個方法/事件介面的實作程式碼。 `IDispEventImpl` 提供的實作`IDispatch`方法。 您只需要提供您有興趣在處理事件的實作。  
  
 `IDispEventImpl` 一起運作的事件接收對應至適當的處理常式函式的路由事件類別中。 若要使用此類別：  
  

 新增[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)巨集，以您想要處理每個物件上的每個事件的事件接收對應。 當使用`IDispEventImpl`複合控制項的基底類別，您可以呼叫[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)若要建立的所有項目在事件接收對應中斷與事件來源的連接。 在其他情況下，或大於控制項中，呼叫[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)之間建立連線的來源物件和基底類別。 呼叫[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)中斷連線。  

  
 您必須衍生自`IDispEventImpl`(使用的唯一值`nID`) 針對每個您要處理事件的物件。 可以取消通知對一個來源物件針對不同的來源物件，然後通知重複使用的基底類別，但可以一次處理單一物件的來源物件的數目上限的數目受限於`IDispEventImpl`基底類別。  
  
 `IDispEventImpl` 提供的相同功能與[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，只不過它會從類型程式庫，而不是需要它的指標當做提供取得有關介面的型別資訊[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)結構。 使用`IDispEventSimpleImpl`當您不要有描述事件介面的型別程式庫或想要避免與使用類型程式庫相關聯的額外負荷。  
  
> [!NOTE]
> `IDispEventImpl` 和`IDispEventSimpleImpl`提供自己的實作**iunknown:: Queryinterface**啟用每個`IDispEventImpl`和`IDispEventSimpleImpl`基底類別做為個別的 COM 識別，同時，仍允許對類別成員中的直接存取您主要的 COM 物件。  
  
 CE ATL 實作 ActiveX 事件接收唯一支援的傳回值類型的 HRESULT 或 void，從您的事件處理常式方法。任何其他傳回值是不支援，且其行為未定義。  
  
 如需詳細資訊，請參閱[支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId  
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
 [in]分派函式的識別碼。  
  
 `lcid`  
 [in]地區設定內容的函式 id。  
  
 `info`  
 [in]結構，表示呼叫函式的方式。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames  
 將單一成員和一組選擇性的引數名稱對應至一組對應的整數可以用於後續呼叫的 Dispid [idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) Windows SDK 中。  
  
##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo  
 擷取物件的類型資訊，可以用來取得介面的類型資訊。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount  
 擷取物件提供的類型資訊介面數目 (0 或 1)。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) Windows SDK 中。  
  
##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType  
 擷取使用者自訂類型的基本類型。  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>參數  
 `pTI`  
 [in]指標[ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680)介面包含使用者定義型別。  
  
 *hrt*  
 [in]要擷取的類型描述控制代碼。  
  
### <a name="return-value"></a>傳回值  
 Variant 類型。  
  
### <a name="remarks"></a>備註  
 請參閱[itypeinfo:: Getreftypeinfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00)。  
  
##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl  
 建構函式。 儲存為類別樣板參數的值`plibid`， `pdiid`， `wMajor`，和`wMinor`。  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>  IDispEventImpl::tihclass  
 此 typedef 是類別範本參數的執行個體`tihclass`。  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>備註  
 根據預設，類別是`CComTypeInfoHolder`。 `CComTypeInfoHolder` 管理類別的類型資訊。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_FUNC_INFO 結構](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl 類別](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](composite-control-macros.md#sink_entry)   
 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [類別概觀](../../atl/atl-class-overview.md)