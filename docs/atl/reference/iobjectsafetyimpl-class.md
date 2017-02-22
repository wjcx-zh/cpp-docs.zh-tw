---
title: "IObjectSafetyImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IObjectSafetyImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [ATL], safe"
  - "IObjectSafety, ATL 實作"
  - "IObjectSafetyImpl class"
  - "safe for scripting and initialization (controls)"
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IObjectSafetyImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 `IObjectSafety` 介面的預設實作允許用戶端擷取和設定物件的安全性層級。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template <class   
      T  
      , DWORD   
      dwSupportedSafety  
      >  
class IObjectSafetyImpl  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `IObjectSafetyImpl`。  
  
 *dwSupportedSafety*  
 指定控制項所支援的安全性選項。  可以是下列其中一個值：  
  
-   應該讓**INTERFACESAFE\_FOR\_UNTRUSTED\_CALLER**[SetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::SetInterfaceSafetyOptions.md) 參數所識別的介面 `riid` 安全性為指令碼。  
  
-   應該讓**INTERFACESAFE\_FOR\_UNTRUSTED\_DATA**`SetInterfaceSafetyOptions` 參數所識別的介面 `riid` 安全對未受信任的資料在初始化時。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::GetInterfaceSafetyOptions.md)|擷取物件所支援的安全性選項，以及為物件目前設定的安全性選項。|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::SetInterfaceSafetyOptions.md)|進行初始化或指令碼物件安全。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[IObjectSafetyImpl::m\_dwCurrentSafety](../Topic/IObjectSafetyImpl::m_dwCurrentSafety.md)|儲存物件的目前的安全性層級。|  
  
## 備註  
 類別提供 `IObjectSafetyImpl``IObjectSafety`的預設實作。  `IObjectSafety` 介面允許用戶端擷取和設定物件的安全性層級。  例如，瀏覽器可以呼叫 **IObjectSafety::SetInterfaceSafetyOptions** 進行初始化的控制指令碼的安全或安全。  
  
 請注意配合 **CATID\_SafeForScripting** 和 **CATID\_SafeForInitializing** 元件分類的 [IMPLEMENTED\_CATEGORY](../Topic/IMPLEMENTED_CATEGORY.md) 巨集提供一種替代方式指定元件是安全的。  
  
 **相關文件** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)， [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## 繼承階層架構  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [IObjectSafety Interface](https://msdn.microsoft.com/en-us/library/aa768224.aspx)   
 [Class Overview](../../atl/atl-class-overview.md)