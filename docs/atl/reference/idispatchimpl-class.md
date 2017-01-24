---
title: "IDispatchImpl Class | Microsoft Docs"
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
  - "IDispatchImpl"
  - "ATL.IDispatchImpl"
  - "ATL::IDispatchImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "雙重介面, 類別"
  - "ATL 中的 IDispatch 類別支援"
  - "IDispatchImpl 類別"
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDispatchImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為雙重介面的 `IDispatch` 組件提供預設實作。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
template<  
   class T,  
   const IID* piid= &__uuidof(T),  
   const GUID* plibid = &CAtlModule::m_libid,  
   WORD wMajor = 1,  
   WORD wMinor = 0,  
   class tihclass = CComTypeInfoHolder   
>   
class ATL_NO_VTABLE IDispatchImpl :  
   public T  
```  
  
#### 參數  
 \[in\] `T`  
 雙重介面。  
  
 \[in\] `piid`  
 為 `T`IID 的指標。  
  
 \[in\] `plibid`  
 其包含有關此介面的資訊型別程式庫的 GUID 的指標。  根據預設，這個伺服器層級的型別程式庫中傳遞。  
  
 \[in\] `wMajor`  
 型別程式庫的主要版本。  預設值為 1。  
  
 \[in\] `wMinor`  
 型別程式庫的次要版本。  預設值為 0。  
  
 \[in\] `tihclass`  
 所使用的類別處理 `T`的型別資訊。  根據預設，這個值為 `CComTypeInfoHolder`。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[IDispatchImpl::IDispatchImpl](../Topic/IDispatchImpl::IDispatchImpl.md)|建構函式。  會在處理雙重介面 \(Dual Interface\) 的型別資訊的受保護成員變數的 `AddRef` 。  解構函式呼叫 `Release`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IDispatchImpl::GetIDsOfNames](../Topic/IDispatchImpl::GetIDsOfNames.md)|將一組名稱對應至一組對應的分派識別項 \(Dispatch Identifier\)。|  
|[IDispatchImpl::GetTypeInfo](../Topic/IDispatchImpl::GetTypeInfo.md)|擷取雙重介面 \(Dual Interface\) 的型別資訊。|  
|[IDispatchImpl::GetTypeInfoCount](../Topic/IDispatchImpl::GetTypeInfoCount.md)|判斷是否有型別資訊的資料為雙重介面。|  
|[IDispatchImpl::Invoke](../Topic/IDispatchImpl::Invoke.md)|提供對雙重介面顯露的方法和屬性的方法。|  
  
## 備註  
 `IDispatchImpl` 對所有雙重介面的 `IDispatch` 組件提供預設實作會在物件。  雙重介面是從 `IDispatch` 衍生並只使用 Automation 相容的型別。  就像分配介面 \(Dispinterface\)，雙重介面支援早期繫結和晚期繫結，不過，雙重介面也支援 vtable 繫結。  
  
 下列範例顯示 `IDispatchImpl` 的一般實作。  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/CPP/idispatchimpl-class_1.h)]  
  
 根據預設， `IDispatchImpl` 類別在註冊的 `T` 搜尋型別資訊。  若要實作未註冊的介面，您可以使用 `IDispatchImpl` 類別，而不需要存取登錄的方法是使用預先定義的版本號碼。  如果您建立含有 0xFFFF 做為 `wMajor` 的值和 0xFFFF 做為 `wMinor`值的 `IDispatchImpl` 物件， `IDispatchImpl` 類別從 .dll 檔案擷取這個型別程式庫 \(而不是註冊。  
  
 `IDispatchImpl` 包含處理雙重介面 \(Dual Interface\) 的型別資訊的型別 `CComTypeInfoHolder` 的靜態成員。  如果您擁有雙重介面實作相同的多個物件，使用 `CComTypeInfoHolder` ，只有一個執行個體。  
  
## 繼承階層架構  
 `T`  
  
 `IDispatchImpl`  
  
## 需求  
 **標題:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)