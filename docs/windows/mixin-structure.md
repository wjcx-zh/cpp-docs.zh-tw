---
title: "MixIn 結構 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::MixIn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MixIn 結構"
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MixIn 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

確定執行階段類別從 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 介面衍生，如果有的話，然後一般 COM 介面。  
  
## 語法  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### 參數  
 `Derived`  
 從 [實作](../windows/implements-structure.md) 結構衍生的型別。  
  
 `MixInType`  
 基底型別。  
  
 `hasImplements`  
 如果 `MixInType` 是從目前實作的基底型別所衍生，則為`true` ；否則 `false` 。  
  
## 備註  
 如果類別衍生自 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和類別 COM 介面，類別宣告清單必須先列出所有 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 介面接著任何傳統 COM 介面。  MixIn 確定介面以正確的順序指定。  
  
## 繼承階層架構  
 `MixIn`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)