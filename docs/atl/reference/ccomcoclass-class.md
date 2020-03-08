---
title: CComCoClass 類別
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 5b4e39fa4d93893d288bb8de03d8a71b671be087
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863164"
---
# <a name="ccomcoclass-class"></a>CComCoClass 類別

這個類別會提供方法來建立類別的實例，以及取得其屬性。

## <a name="syntax"></a>語法

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自 `CComCoClass`的類別。

*pclsid*<br/>
物件 CLSID 的指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCoClass：： CreateInstance](#createinstance)|靜止建立類別的實例，並查詢介面。|
|[CComCoClass：： Error](#error)|靜止傳回豐富的錯誤資訊給用戶端。|
|[CComCoClass：： GetObjectCLSID](#getobjectclsid)|靜止傳回物件的類別識別碼。|
|[CComCoClass：： GetObjectDescription](#getobjectdescription)|靜止覆寫以傳回物件的描述。|

## <a name="remarks"></a>備註

`CComCoClass` 提供方法來抓取物件的 CLSID、設定錯誤資訊，以及建立類別的實例。 在物件對應中註冊的任何類別都應該衍生自 `CComCoClass`。

`CComCoClass` 也會定義物件的預設 Class Factory 和匯總模型。 `CComCoClass` 使用下列兩個宏：

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)宣告要[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)的 Class Factory。

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)宣告您的物件可以匯總。

您可以藉由在類別定義中指定另一個宏，覆寫其中一個預設值。 例如，若要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不是 `CComClassFactory`，請指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="createinstance"></a>CComCoClass：： CreateInstance

使用這些 `CreateInstance` 函式來建立 COM 物件的實例，並在不使用 COM API 的情況下取出介面指標。

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>參數

*Q*<br/>
應該透過*pp*傳回的 COM 介面。

*punkOuter*<br/>
在外部不明或控制不明的匯總。

*換*<br/>
脫銷當建立成功時，接收要求之介面指標的指標變數位址。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。 如需可能傳回值的描述，請參閱 Windows SDK 中的[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) 。

### <a name="remarks"></a>備註

使用此函式的第一個多載來建立一般物件;當您需要匯總所建立的物件時，請使用第二個多載。

執行必要 COM 物件（也就是當做[CComCoClass](../../atl/reference/ccomcoclass-class.md)的第一個樣板參數使用的類別）的 ATL 類別必須與呼叫程式碼位於相同的專案中。 COM 物件的建立是由針對此 ATL 類別註冊的 Class Factory 執行。

這些函式可用於建立您無法使用[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)宏從外部建立的物件。 當您想要基於效率的原因來避免 COM API 時，這些功能也很有用。

請注意，介面*Q*必須具有與其相關聯的 IID，可以使用[__uuidof](../../cpp/uuidof-operator.md)運算子來抓取。

### <a name="example"></a>範例

在下列範例中，`CDocument` 是從執行 `IDocument` 介面的 `CComCoClass` 衍生的 wizard 產生的 ATL 類別。 類別會使用 OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 宏在物件對應中註冊，讓用戶端無法使用[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)建立檔的實例。 `CApplication` 是 CoClass，它會在其中一個自己的 COM 介面上提供方法，以建立檔類別的實例。 下列程式碼顯示如何使用繼承自 `CComCoClass` 基類的 `CreateInstance` 成員，輕鬆地建立檔類別的實例。

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>CComCoClass：： Error

此靜態函式會設定 `IErrorInfo` 介面，以提供錯誤資訊給用戶端。

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

*lpszDesc*<br/>
在描述錯誤的字串。 Unicode 版本的 `Error` 指定*lpszDesc*的類型為 LPCOLESTR;ANSI 版本會指定 LPCSTR 的類型。

*iid*<br/>
在定義錯誤的介面的 IID，或如果作業系統定義錯誤，則為 GUID_Null （預設值）。

*hRes*<br/>
在您想要傳回給呼叫者的 HRESULT。 預設值為 0。 如需*hRes*的詳細資訊，請參閱備註。

*nID*<br/>
在儲存錯誤描述字串的資源識別碼。 這個值應介於0x0200 與0xFFFF （含）之間。 在 debug 組建中，如果*nID*未編制有效字串的索引 **，就會產生判斷**提示。 在發行組建中，錯誤描述字串會設定為「未知的錯誤」。

*dwHelpID*<br/>
在錯誤的說明內容識別碼。

*lpszHelpFile*<br/>
在描述錯誤之說明檔的路徑和名稱。

*hInst*<br/>
在資源的控制碼。 根據預設，此參數為 `_AtlModule::GetResourceInstance`，其中 `_AtlModule` 是[CAtlModule](../../atl/reference/catlmodule-class.md)的全域實例。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

若要呼叫 `Error`，您的物件必須執行 `ISupportErrorInfo Interface` 介面。

如果*hRes*參數不是零，則 `Error` 會傳回*hRes*的值。 如果*hRes*為零，則 `Error` 的前四個版本會傳回 DISP_E_EXCEPTION。 最後兩個版本會傳回宏的結果**MAKE_HRESULT （1，FACILITY_ITF，** *nID* **）** 。

##  <a name="getobjectclsid"></a>CComCoClass：： GetObjectCLSID

提供一種一致的方式來抓取物件的 CLSID。

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>傳回值

物件的類別識別碼。

##  <a name="getobjectdescription"></a>CComCoClass：： GetObjectDescription

這個靜態函式會抓取類別物件的文字描述。

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>傳回值

類別物件的描述。

### <a name="remarks"></a>備註

預設的實值會傳回 Null。 您可以使用[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)宏來覆寫這個方法。 例如，

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`IComponentRegistrar::GetComponents`會呼叫 `GetObjectDescription`。 `IComponentRegistrar` 是自動化介面，可讓您註冊及取消註冊 DLL 中的個別元件。 當您使用 ATL 專案 Wizard 建立元件註冊機構物件時，嚮導會自動執行 `IComponentRegistrar` 介面。 `IComponentRegistrar` 通常是由 Microsoft 交易伺服器所使用。

如需 ATL 專案 Wizard 的詳細資訊，請參閱[建立 Atl 專案一](../../atl/reference/creating-an-atl-project.md)文。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
