---
title: "ISupportErrorInfoImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::ISupportErrorInfoImpl<piid>"
  - "ATL::ISupportErrorInfoImpl"
  - "ISupportErrorInfoImpl"
  - "ATL.ISupportErrorInfoImpl<piid>"
  - "ATL.ISupportErrorInfoImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error information, ATL"
  - "ISupportErrorInfo ATL implementation"
  - "ISupportErrorInfoImpl class"
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ISupportErrorInfoImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當只有單一介面在物件時會產生錯誤，這個類別會提供 [ISupportErrorInfo Interface](http://msdn.microsoft.com/zh-tw/42d33066-36b4-4a5b-aa5d-46682e560f32) 的預設實作，而且可以使用。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
const IID* piid   
>  
class ATL_NO_VTABLE ISupportErrorInfoImpl :  
public ISupportErrorInfo  
```  
  
#### 參數  
 `piid`  
 為支援 [IErrorInfo](http://msdn.microsoft.com/zh-tw/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)介面的 IID 的指標。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](../Topic/ISupportErrorInfoImpl::InterfaceSupportsErrorInfo.md)|表示 `riid` 判斷介面是否支援 [IErrorInfo](http://msdn.microsoft.com/zh-tw/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) 介面。|  
  
## 備註  
 [ISupportErrorInfo Interface](http://msdn.microsoft.com/zh-tw/42d33066-36b4-4a5b-aa5d-46682e560f32) 確定錯誤訊息可能傳回給用戶端。  使用 **IErrorInfo** 的物件必須實作 **ISupportErrorInfo**。  
  
 當只有單一介面在物件時，會產生錯誤 `ISupportErrorInfoImpl`**ISupportErrorInfo** 類別所提供的預設實作，而且可以使用。  例如：  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/CPP/isupporterrorinfoimpl-class_1.h)]  
  
## 繼承階層架構  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)