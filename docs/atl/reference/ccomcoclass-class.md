---
title: CComCo 類
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
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320829"
---
# <a name="ccomcoclass-class"></a>CComCo 類

此類提供用於創建類實例和獲取其屬性的方法。

## <a name="syntax"></a>語法

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`CComCoClass`。

*pclsid*<br/>
指向物件的 CLSID 的指標。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCoClass:建立實體](#createinstance)|(靜態)為介面創建類和查詢的實例。|
|[CComCoClass:錯誤](#error)|(靜態)將豐富的錯誤資訊返回給用戶端。|
|[CComCoClass:取得物件CLSID](#getobjectclsid)|(靜態)返回物件的類標識碼。|
|[CComCoClass::取得物件描述](#getobjectdescription)|(靜態)覆蓋以返回對象的說明。|

## <a name="remarks"></a>備註

`CComCoClass`提供了檢索物件的 CLSID、設置錯誤資訊和創建類實例的方法。 在物件映射中註冊的任何類都應派生自`CComCoClass`。

`CComCoClass`還定義了對象的預設類工廠和聚合模型。 `CComCoClass`使用以下兩個巨集:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)宣告類別為[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)聲明可以聚合物件。

您可以通過在類定義中指定另一個宏來覆蓋這些預設值中的任何一個。 例如,要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`,請指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass:建立實體

使用這些`CreateInstance`函數創建 COM 物件的實例,並在不使用 COM API 的情況下檢索介面指標。

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>參數

*Q*<br/>
應透過*pp*返回的 COM 介面。

*龐克外*<br/>
[在]聚合的外部未知或控制未知。

*Pp*<br/>
[出]如果創建成功,接收請求的介面指標的指標變數的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。 有關可能的返回值的說明,請參閱 Windows SDK 中的[CoCreateInstance。](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)

### <a name="remarks"></a>備註

使用此函數的第一個重載來創建典型物件;當您需要聚合正在創建的物件時,請使用第二個重載。

實現所需 COM 物件的 ATL 類(即用作[CComCoClass](../../atl/reference/ccomcoclass-class.md)的第一個樣本參數的類)必須與調用代碼位於同一專案中。 COM 物件的創建由為此 ATL 類註冊的類工廠執行。

這些函數可用於創建通過使用[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)宏阻止外部可創建的物件。 它們在您希望出於效率原因避免 COM API 的情況下也很有用。

請注意,介面*Q*必須具有與其關聯的 IID,可以使用[__uuidof](../../cpp/uuidof-operator.md)運算符檢索。

### <a name="example"></a>範例

在下面的範例中,`CDocument`是從實現`CComCoClass`介面的精靈生成的 ATL 類派生`IDocument`的。 類在物件映射中註冊了OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO宏,因此客戶端無法使用[CoCreate 實例](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)創建文檔實例。 `CApplication`CoClass 在其自己的 COM 介面中提供方法以創建文檔類的實例。 下面的代碼顯示了使用從`CreateInstance``CComCoClass`基類繼承的成員創建文檔類實例的簡便性。

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CComCoClass:錯誤

此靜態函數設置`IErrorInfo`介面以向用戶端提供錯誤資訊。

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
[在]描述錯誤的字串。 的`Error`Unicode 版本指定*lpszDesc*的類型為 LPCOLESTR;ANSI 版本指定 LPCSTR 的類型。

*Iid*<br/>
[在]如果錯誤由操作系統定義,則定義錯誤的介面的 IID 或GUID_NULL(預設值)。

*hRes*<br/>
[在]要返回給調用方的 HRESULT。 預設值為 0。 有關*hRe 的更多*詳細資訊,請參閱備註。

*nID*<br/>
[在]儲存錯誤描述字串的資源識別碼。 此值應介於 0x0200 和 0xFF 之間(包括)。 在除錯產生中,如果*nID*不索引有效字串,則會產生**ASSERT。** 在發佈版本中,錯誤描述字串將設置為"未知錯誤"。

*dwHelpID*<br/>
[在]錯誤的説明上下文標識碼。

*lpszHelp 檔案*<br/>
[在]描述錯誤的幫助檔的路徑和名稱。

*hInst*<br/>
[在]資源的句柄。 預設情況下,此參數是`_AtlModule::GetResourceInstance``_AtlModule` [,CAtlModule](../../atl/reference/catlmodule-class.md)的全域實例就是 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

要調用`Error`,對象`ISupportErrorInfo Interface`必須實現介面。

如果*hRes*參數是非零`Error`,則返回*hRes*的值。 如果*hRes*為零`Error`,則返回的前四個版本DISP_E_EXCEPTION。 最後兩個版本返回宏**MAKE_HRESULT的結果(1、FACILITY_ITF、nID** *nID* **)。**

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass:取得物件CLSID

提供了檢索物件的 CLSID 的一致方法。

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>傳回值

物件的類標識碼。

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass::取得物件描述

此靜態函數檢索類對象的文本說明。

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>傳回值

類對象的描述。

### <a name="remarks"></a>備註

預設實現返回 NULL。 您可以使用[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)宏重寫此方法。 例如：

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`由`IComponentRegistrar::GetComponents`呼叫 。 `IComponentRegistrar`是一個自動化介面,允許您在 DLL 中註冊和取消註冊單個元件。 使用 ATL 專案精靈創建元件註冊器物件時,嚮導將自動實現`IComponentRegistrar`介面。 `IComponentRegistrar`通常用於 Microsoft 事務伺服器。

有關 ATL 專案精靈的詳細資訊,請參閱創建[ATL 專案](../../atl/reference/creating-an-atl-project.md)的文章。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
