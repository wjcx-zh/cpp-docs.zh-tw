---
title: "ArgTraitsHelper 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::ArgTraitsHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ArgTraitsHelper 結構"
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ArgTraitsHelper 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template<  
   typename TDelegateInterface  
>  
struct ArgTraitsHelper;  
```  
  
#### 參數  
 `TDelegateInterface`  
 委派介面。  
  
## 備註  
 幫助定義委派引數的一般特性。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`methodType`|`decltype(&TDelegateInterface::Invoke)`的一個同義資料表。|  
|`Traits`|`ArgTraits<methodType>`的一個同義資料表。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[ArgTraitsHelper::args 常數](../windows/argtraitshelper-args-constant.md)|協助 [ArgTraitsHelper::args](../windows/argtraits-args-constant.md) 計數參數中委派叫用介面的方法的數目。|  
  
## 繼承階層架構  
 `ArgTraitsHelper`  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)