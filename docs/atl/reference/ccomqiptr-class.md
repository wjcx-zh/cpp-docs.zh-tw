---
title: "CComQIPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComQIPtr"
  - "ATL::CComQIPtr"
  - "CComQIPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComQIPtr class"
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComQIPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理的 COM 介面指標的智慧型指標類別。  
  
## 語法  
  
```  
  
      template<  
   class T,  
   const IID* piid = &__uuidof(T)  
>  
class CComQIPtr: public CComPtr<T>  
```  
  
#### 參數  
 `T`  
 指定指標型別 COM 介面的值。  
  
 `piid`  
 為 `T`IID 的指標。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)|建構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComQIPtr::operator \=](../Topic/CComQIPtr::operator%20=.md)|將成員指標的指標。|  
  
## 備註  
 ATL 會 `CComQIPtr` 和 [CComPtr](../../atl/reference/ccomptr-class.md) 處理 COM 介面指標，這兩者 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)從衍生。  這兩個類別執行計算藉由呼叫的自動參考 `AddRef` 和 **版本**。  多載運算子 Managed 指標作業。  
  
## 繼承階層架構  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## 需求  
 **Header:** atlcomcli.h  
  
## 請參閱  
 [CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)   
 [CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)   
 [CComPtrBase Class](../../atl/reference/ccomptrbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)