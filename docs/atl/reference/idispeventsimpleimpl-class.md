---
title: "IDispEventSimpleImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDispEventSimpleImpl"
  - "ATL::IDispEventSimpleImpl"
  - "ATL.IDispEventSimpleImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventSimpleImpl class"
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDispEventSimpleImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 `IDispatch` 方法的實作，而不用，取得型別資訊從型別程式庫。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
UINT nID,  
class T,  
const IID* pdiid  
>  
class ATL_NO_VTABLE IDispEventSimpleImpl :  
public _IDispEventLocator<nID, pdiid>  
```  
  
#### 參數  
 `nID`  
 來源物件的唯一識別項。  當 `IDispEventSimpleImpl` 是複合控制項的基底類別，則這個參數會使用所包含的控制項的資源 ID。  在其他情況下，請使用選擇性的正整數。  
  
 `T`  
 使用者的類別， `IDispEventSimpleImpl`從衍生。  
  
 `pdiid`  
 為這個類別會實作事件的分派介面的 IID 的指標。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IDispEventSimpleImpl::Advise](../Topic/IDispEventSimpleImpl::Advise.md)|建立具有預設事件來源的連結。|  
|[IDispEventSimpleImpl::DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)|建立事件來源的連結。|  
|[IDispEventSimpleImpl::DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md)|中斷與事件來源的連結。|  
|[IDispEventSimpleImpl::GetIDsOfNames](../Topic/IDispEventSimpleImpl::GetIDsOfNames.md)|傳回 **E\_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfo](../Topic/IDispEventSimpleImpl::GetTypeInfo.md)|傳回 **E\_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfoCount](../Topic/IDispEventSimpleImpl::GetTypeInfoCount.md)|傳回 **E\_NOTIMPL**。|  
|[IDispEventSimpleImpl::Invoke](../Topic/IDispEventSimpleImpl::Invoke.md)|在事件接收對應呼叫事件處理常式清單。|  
|[IDispEventSimpleImpl::Unadvise](../Topic/IDispEventSimpleImpl::Unadvise.md)|中斷與預設事件來源的連結。|  
  
## 備註  
 `IDispEventSimpleImpl` 提供實作事件介面 \(Dispinterface\) 模式，而不會要求您提供每個方法\/事件的程式碼實作該介面。  `IDispEventSimpleImpl``IDispatch` 提供方法的實作。  您只需要提供事件實作要處理有興趣。  
  
 使用 [事件接收對應](../Topic/BEGIN_SINK_MAP.md)`IDispEventSimpleImpl` 工作中的路由事件的類別為適當的處理常式函式。  使用這個類別:  
  
-   將 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md) 巨集加入至每個事件的事件接收對應於您要管理的每個物件。  
  
-   每個事件所提供的型別資訊傳遞指標 [\_ATL\_FUNC\_INFO](../../atl/reference/atl-func-info-structure.md) 結構當做參數傳遞至每一個項目。  在 x86 平台上， `_ATL_FUNC_INFO.cc` 值必須與呼叫方法不符的回呼函式的 CC\_CDECL。  
  
-   呼叫建立來源物件和基底類別之間的連接 [DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md) 。  
  
-   呼叫會中斷連接的 [DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) 。  
  
 您必須從 `IDispEventSimpleImpl` 衍生 \(使用 `nID`的唯一值\) 您必須處理事件之物件的。  您可以 unadvising 重複使用基底類別對來源物件然後建議對不同的來源物件，但是，來源的物件最大數目可能由單一物件一次處理 `IDispEventSimpleImpl` 基底類別的數量。  
  
 **IDispEventSimplImpl** 提供功能和 [IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，不同的是，它會從型別程式庫中未取得介面的型別資訊。  精靈會根據 `IDispEventImpl`只的程式碼，不過，您可以手動加入程式碼以使用 `IDispEventSimpleImpl` 。  當您沒有型別描述事件介面的類別庫也不要避免此額外負荷與使用型別程式庫時，請使用 `IDispEventSimpleImpl` 。  
  
> [!NOTE]
>  `IDispEventImpl` 和 `IDispEventSimpleImpl`**IUnknown::QueryInterface** 提供它們自己的實作可讓每一 `IDispEventImpl` 或 `IDispEventSimpleImpl` 基底類別當做個別的 COM 識別，仍允許對類別成員的直接存取您的主要 COM 物件中的紀元。  
  
 CE ActiveX 事件接收的 ATL 實作只支援傳回值與您的事件處理常式方法的 HRESULT 或 void 型別;其他傳回值不受支援，而且它的行為會是未定義的。  
  
 如需詳細資訊，請參閱 [支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## 繼承階層架構  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [\_ATL\_FUNC\_INFO Structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl Class](../../atl/reference/idispeventimpl-class.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)   
 [Class Overview](../../atl/atl-class-overview.md)