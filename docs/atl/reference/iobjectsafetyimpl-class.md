---
title: "IObjectSafetyImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: cdcc008797e94988fb42fd6239603fa300a84233
ms.contentlocale: zh-tw
ms.lasthandoff: 03/31/2017

---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl 類別
這個類別提供的預設實作`IObjectSafety`介面，以允許用戶端會擷取和設定物件的安全性層級。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template <class T,DWORD dwSupportedSafety>  
class IObjectSafetyImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IObjectSafetyImpl`。  
  
 *dwSupportedSafety*  
 指定控制項的支援的安全性選項。 可為下列其中一個值：  
  
- **INTERFACESAFE_FOR_UNTRUSTED_CALLER**所識別的介面[SetInterfaceSafetyOptions](#setinterfacesafetyoptions)參數`riid`應該設定成可安全用於指令碼。  
  
- **INTERFACESAFE_FOR_UNTRUSTED_DATA**所識別的介面`SetInterfaceSafetyOptions`參數`riid`應該設定成安全的未受信任的資料在初始化期間。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|擷取物件所支援的安全性選項，以及目前的物件設定的安全性選項。|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|使物件來初始化或指令碼的安全。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|儲存物件的目前安全性層級。|  
  
## <a name="remarks"></a>備註  
 類別`IObjectSafetyImpl`提供的預設實作`IObjectSafety`。 `IObjectSafety`介面可讓用戶端會擷取和設定物件的安全性層級。 例如，網頁瀏覽器可以呼叫**IObjectSafety::SetInterfaceSafetyOptions**來設定該控制項用於初始化安全或安全用於指令碼。  
  
 請注意，使用[IMPLEMENTED_CATEGORY](category-macros.md#implemented_category)巨集透過**CATID_SafeForScripting**和**CATID_SafeForInitializing**元件類別提供指定的元件安全的替代方式。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions  
 擷取物件所支援的安全性選項，以及目前的物件設定的安全性選項。  
  
```
HRESULT GetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```  
  
### <a name="remarks"></a>備註  
 實作會傳回適當的值物件的實作所支援的任何介面**iunknown:: Queryinterface**。  
  
> [!IMPORTANT]
>  支援的任何物件`IObjectSafety`負責它自己的安全性，則會將委派的任何物件。 程式設計人員必須納入帳戶問題所引起的使用者內容中執行程式碼、 跨網站指令碼，並且執行適當的區域檢查。  
  
 請參閱[IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety  
 儲存物件的目前安全性層級。  
  
```
DWORD m_dwCurrentSafety;
```  
  
##  <a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions  
 使物件初始化，或藉由設定指令碼的安全[m_dwCurrentSafety](#m_dwcurrentsafety)成員為適當的值。  
  
```
HRESULT SetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```  
  
### <a name="remarks"></a>備註  
 實作會傳回**E_NOINTERFACE**物件的實作不支援任何介面**iunknown:: Queryinterface**。  
  
> [!IMPORTANT]
>  支援的任何物件`IObjectSafety`負責它自己的安全性，則會將委派的任何物件。 程式設計人員必須納入帳戶問題所引起的使用者內容中執行程式碼、 跨網站指令碼，並且執行適當的區域檢查。  
  
 請參閱[IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IObjectSafety 介面](https://msdn.microsoft.com/library/aa768224.aspx)   
 [類別概觀](../../atl/atl-class-overview.md)

