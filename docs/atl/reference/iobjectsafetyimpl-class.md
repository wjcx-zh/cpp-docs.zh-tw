---
title: IObjectSafetyimpl 類別
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329655"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyimpl 類別

此類提供介面的預設實現,`IObjectSafety`以允許用戶端檢索和設置物件的安全級別。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IObjectSafetyImpl`。

*dw支援安全*<br/>
指定控制項的支援安全選項。 可以是下列其中一個值：

- INTERFACESAFE_FOR_UNTRUSTED_CALLER [SetInterface 安全選項](#setinterfacesafetyoptions)參數`riid`標識的介面應使腳本編寫安全。

- INTERFACESAFE_FOR_UNTRUSTED_DATA 參數標識`SetInterfaceSafetyOptions`的`riid`介面應在初始化期間對不受信任的數據提供安全。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IObjectSafetyimpl::取得介面安全選項](#getinterfacesafetyoptions)|檢索物件支援的安全選項以及當前為物件設置的安全選項。|
|[IObjectSafetyimpl::設定介面安全選項](#setinterfacesafetyoptions)|使物件安全進行初始化或腳本化。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IObjectSafetyimpl::m_dwCurrentSafety](#m_dwcurrentsafety)|存儲物件的當前安全級別。|

## <a name="remarks"></a>備註

類`IObjectSafetyImpl`提供`IObjectSafety`的默認實現。 該`IObjectSafety`介面允許用戶端檢索和設置物件的安全級別。 例如,Web 瀏覽器可以調`IObjectSafety::SetInterfaceSafetyOptions`用 以使控制項安全用於初始化或腳本編寫安全。

請注意,將[IMPLEMENTED_CATEGORY](category-macros.md#implemented_category)宏與CATID_SafeForScripting和CATID_SafeForInitializing元件類別一起使用提供了指定元件安全的替代方法。

**相關文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md), 建立[ATL 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyimpl::取得介面安全選項

檢索物件支援的安全選項以及當前為物件設置的安全選項。

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>備註

實現返回物件實現 支援的任何介面的`IUnknown::QueryInterface`適當值。

> [!IMPORTANT]
> 支援`IObjectSafety`的任何物件都負責其自身的安全性及其委託的任何對象的安全性。 程序員必須考慮在使用者上下文中運行代碼、跨網站腳本和執行適當的區域檢查所產生的問題。

請參閱[IObject 安全:獲取](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\))Windows SDK 中的介面安全選項。

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyimpl::m_dwCurrentSafety

存儲物件的當前安全級別。

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyimpl::設定介面安全選項

通過將[m_dwCurrentSafety](#m_dwcurrentsafety)成員設置為適當的值,使物件在初始化或腳本化方面安全。

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>備註

對於物件實現 不支援的任何介面,實現`IUnknown::QueryInterface`返回E_NOINTERFACE。

> [!IMPORTANT]
> 支援`IObjectSafety`的任何物件都負責其自身的安全性及其委託的任何對象的安全性。 程序員必須考慮在使用者上下文中運行代碼、跨網站腳本和執行適當的區域檢查所產生的問題。

請參閱[IObject 安全:在](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\))Windows SDK 中設置介面安全選項。

## <a name="see-also"></a>另請參閱

[IObject 安全介面](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[類別概觀](../../atl/atl-class-overview.md)
