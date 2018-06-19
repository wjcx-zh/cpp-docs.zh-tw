---
title: CComCoClass 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
dev_langs:
- C++
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 738d7e937acf2d3299be97b4f091c698582911d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365458"
---
# <a name="ccomcoclass-class"></a>CComCoClass 類別
這個類別會提供方法來建立執行個體的類別，並取得其屬性。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`CComCoClass`。  
  
 *pclsid*  
 物件的 CLSID 指標。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|（靜態）建立類別和介面查詢的執行個體。|  
|[CComCoClass::Error](#error)|（靜態）傳回用戶端豐富的錯誤資訊。|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|（靜態）傳回物件的類別識別項。|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|（靜態）覆寫以傳回物件的描述。|  
  
## <a name="remarks"></a>備註  
 `CComCoClass` 提供方法來擷取物件的 CLSID、 設定資訊時發生錯誤，以及建立類別的執行個體。 在中註冊的任何類別[物件對應](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f)應該衍生自`CComCoClass`。  
  
 `CComCoClass` 也會定義物件的預設類別處理站和彙總模型。 `CComCoClass` 使用下列兩個巨集：  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)宣告 class factory 是[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)宣告您的物件可以彙總。  
  
 您可以在類別定義中指定其他巨集來覆寫其中一個這些預設值設定。 例如，若要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)巨集：  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="createinstance"></a>  CComCoClass::CreateInstance  
 使用這些`CreateInstance`函式來建立執行個體的 COM 物件，並擷取介面指標，而不需要使用 COM API。  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>參數  
 `Q`  
 應該透過傳回的 COM 介面`pp`。  
  
 *punkOuter*  
 [in]外部未知或控制未知的彙總。  
  
 `pp`  
 [out]如果成功建立接收要求的介面指標的指標變數的位址。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。 請參閱[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) Windows SDK 中針對可能的傳回值的描述。  
  
### <a name="remarks"></a>備註  
 用於建立一般的物件; 此函式的第一個多載當您需要彙總所建立的物件時，請使用第二個多載。  
  
 實作必要的 COM 物件的 ATL 類別 (也就是做為第一個範本參數的類別[CComCoClass](../../atl/reference/ccomcoclass-class.md)) 必須在與呼叫程式碼相同的專案。 建立 COM 物件是由這個 ATL 類別註冊的 class factory 執行。  
  
 這些函式可用於建立具有會防止您正在使用的從外部建立的物件[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)巨集。 它們也是您要避免 COM API，效率的原因很有用。  
  
 請注意，介面`Q`必須具有與其相關聯，可以使用擷取的 IID [__uuidof](../../cpp/uuidof-operator.md)運算子。  
  
### <a name="example"></a>範例  
 在下列範例中，`CDocument`精靈產生的 ATL 類別衍生自`CComCoClass`實作**IDocument**介面。 類別會在與物件對應中註冊`OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`巨集，因此用戶端無法建立文件使用的執行個體[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。 `CApplication` 是提供一種方法其中一個自己的 COM 介面來建立文件類別的執行個體的 CoClass。 示範如何輕鬆將下列程式碼，以便建立文件類別使用的執行個體`CreateInstance`成員繼承自`CComCoClass`基底類別。  
  
 [!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="error"></a>  CComCoClass::Error  
 此靜態函式中設定`IErrorInfo`介面，以提供給用戶端的資訊時發生錯誤。  
  
```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>參數  
 `lpszDesc`  
 [in]描述錯誤的字串。 Unicode 版本`Error`指定`lpszDesc`的型別**LPCOLESTR**; ANSI 版本指定一種`LPCSTR`。  
  
 `iid`  
 [in]定義錯誤之介面的 IID 或`GUID_NULL`（預設值） 如果錯誤由作業系統所定義。  
  
 `hRes`  
 [in]`HRESULT`您想要傳回給呼叫者。 預設值為 0。 如需詳細資訊`hRes`，請參閱 < 備註 >。  
  
 `nID`  
 [in]儲存錯誤描述字串資源的識別項。 這個值應該介於 0x0200 和 0xFFFF 之間 （含） 之間。 在偵錯組建**ASSERT**如果將會產生`nID`未索引的有效字串。 在發行組建中的錯誤描述字串將會設定為 「 未知的錯誤 」。  
  
 `dwHelpID`  
 [in]錯誤的說明內容識別碼。  
  
 `lpszHelpFile`  
 [in]路徑和名稱，描述錯誤的說明檔。  
  
 `hInst`  
 [in]資源控制代碼。 根據預設，這個參數是 **_AtlModule::GetResourceInstance**，其中**接在 _AtlModule**的全域執行個體[CAtlModule](../../atl/reference/catlmodule-class.md)。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 若要呼叫`Error`，您的物件必須實作`ISupportErrorInfo Interface`介面。  
  
 如果`hRes`參數不是零，然後`Error`傳回的值`hRes`。 如果`hRes`是零，則前四個新版`Error`傳回`DISP_E_EXCEPTION`。 最後兩個版本都會傳回巨集的結果**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。  
  
##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID  
 提供一致的方式來擷取物件的 CLSID。  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>傳回值  
 物件的類別識別項。  
  
##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription  
 此靜態函式會擷取您的類別物件的文字描述。  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>傳回值  
 類別物件的描述。  
  
### <a name="remarks"></a>備註  
 預設實作會傳回**NULL**。 您可以覆寫這個方法與[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)巨集。 例如:   
  
 [!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription` 會呼叫**IComponentRegistrar::GetComponents**。 **IComponentRegistrar**是一種自動化的介面，可讓您註冊及取消註冊 DLL 中的個別元件。 當您建立元件的註冊機構物件使用 ATL 專案精靈 」 時，精靈會自動實作**IComponentRegistrar**介面。 **IComponentRegistrar**通常由 Microsoft Transaction Server。  
  
 如需 ATL 專案精靈的詳細資訊，請參閱文章[ATL 專案建立](../../atl/reference/creating-an-atl-project.md)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
