---
title: "IDispEventImpl Class | Microsoft Docs"
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
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventImpl class"
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDispEventImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供 `IDispatch` 方法的實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
UINT nID,  
class T,  
const IID* pdiid= &IID_NULL,  
const GUID* plibid= &GUID_NULL,  
WORD wMajor= 0,  
WORD wMinor= 0,  
class tihclass= CcomTypeInfoHolder  
>  
class ATL_NO_VTABLE IDispEventImpl :  
public IDispEventSimpleImpl<nID, T, pdiid>  
```  
  
#### 參數  
 `nID`  
 來源物件的唯一識別項。  當 `IDispEventImpl` 是複合控制項的基底類別，則這個參數會使用所包含的控制項的資源 ID。  在其他情況下，請使用選擇性的正整數。  
  
 `T`  
 使用者的類別， `IDispEventImpl`從衍生。  
  
 `pdiid`  
 為這個類別會實作事件的分派介面的 IID 的指標。  在這個型別 `plibid`、 `wMajor`和 `wMinor`運算式的程式庫必須定義這個介面。  
  
 `plibid`  
 物件的分派介面的型別程式庫的指標所指向的 `pdiid`。  如果 **\_&GUID\_NULL**，將型別程式庫從物件來源號會載入事件。  
  
 `wMajor`  
 型別程式庫的主要版本。  預設值為 0。  
  
 `wMinor`  
 型別程式庫的次要版本。  預設值為 0。  
  
 `tihclass`  
 所使用的類別處理 `T`的型別資訊。  預設值為型別 `CComTypeInfoHolder`類別;不過，刪除 `CComTypeInfoHolder`之外，您也可以藉由提供型別的類別會覆寫這個樣板參數。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[IDispEventImpl::\_tihclass](../../atl/reference/idispeventimpl-class.md)|用於類別處理型別資訊。  預設值為 `CComTypeInfoHolder`。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[IDispEventImpl::IDispEventImpl](../Topic/IDispEventImpl::IDispEventImpl.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IDispEventImpl::GetFuncInfoFromId](../Topic/IDispEventImpl::GetFuncInfoFromId.md)|設定指定的分派識別項索引的函式。|  
|[IDispEventImpl::GetIDsOfNames](../Topic/IDispEventImpl::GetIDsOfNames.md)|將單一成員和一組選擇性引數名稱對應至一組整數 DispId。|  
|[IDispEventImpl::GetTypeInfo](../Topic/IDispEventImpl::GetTypeInfo.md)|擷取物件的型別資訊。|  
|[IDispEventImpl::GetTypeInfoCount](../Topic/IDispEventImpl::GetTypeInfoCount.md)|擷取型別資訊介面數目。|  
|[IDispEventImpl::GetUserDefinedType](../Topic/IDispEventImpl::GetUserDefinedType.md)|擷取使用者定義型別的基底型別。|  
  
## 備註  
 `IDispEventImpl` 提供實作事件介面 \(Dispinterface\) 模式，而不會要求您提供每個方法\/事件的程式碼實作該介面。  `IDispEventImpl``IDispatch` 提供方法的實作。  您只需要提供事件實作要處理有興趣。  
  
 使用 [事件接收對應](../Topic/BEGIN_SINK_MAP.md)`IDispEventImpl` 工作中的路由事件的類別為適當的處理常式函式。  使用這個類別:  
  
 將 [SINK\_ENTRY](../Topic/SINK_ENTRY.md) 或 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md) 巨集加入至每個事件的事件接收對應於您要管理的每個物件。  當使用 `IDispEventImpl` 為複合控制項的基底類別時，您可以在事件接收對應可以呼叫 [AtlAdviseSinkMap](../Topic/AtlAdviseSinkMap.md) 建立和中斷與事件來源連接中所有項目的。  在某些情況下，或取得更大的控制項，呼叫建立來源物件和基底類別之間的連接 [DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md) 。  呼叫會中斷連接的 [DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) 。  
  
 您必須從 `IDispEventImpl` 衍生 \(使用 `nID`的唯一值\) 您必須處理事件之物件的。  您可以 unadvising 重複使用基底類別對來源物件然後建議對不同的來源物件，但是，來源的物件最大數目可能由單一物件一次處理 `IDispEventImpl` 基底類別的數量。  
  
 `IDispEventImpl` 提供功能和 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，不同的是，它會從型別程式庫來取得介面的型別資訊而不要讓它提供做為指標。 [\_ATL\_FUNC\_INFO](../../atl/reference/atl-func-info-structure.md) 結構。  當您沒有型別描述事件介面的類別庫也不要避免此額外負荷與使用型別程式庫時，請使用 `IDispEventSimpleImpl` 。  
  
> [!NOTE]
>  `IDispEventImpl` 和 `IDispEventSimpleImpl`**IUnknown::QueryInterface** 提供它們自己的實作可讓每一 `IDispEventImpl` 和 `IDispEventSimpleImpl` 基底類別當做個別的 COM 識別，仍允許對類別成員的直接存取您的主要 COM 物件中的紀元。  
  
 CE ActiveX 事件接收的 ATL 實作只支援傳回值與您的事件處理常式方法的 HRESULT 或 void 型別;其他傳回值不受支援，而且它的行為會是未定義的。  
  
 如需詳細資訊，請參閱 [支援 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## 繼承階層架構  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [\_ATL\_FUNC\_INFO Structure](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl Class](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK\_ENTRY](../Topic/SINK_ENTRY.md)   
 [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md)   
 [SINK\_ENTRY\_INFO](../Topic/SINK_ENTRY_INFO.md)   
 [Class Overview](../../atl/atl-class-overview.md)