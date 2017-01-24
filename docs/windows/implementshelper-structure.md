---
title: "ImplementsHelper 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ImplementsHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ImplementsHelper 結構"
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ImplementsHelper 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### 參數  
 `RuntimeClassFlagsT`  
 指定一或多個 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值旗標的欄位。  
  
 `ILst`  
 介面 ID 的清單。  
  
 `IsDelegateToClass`  
 如果目前的執行個體是在`ILst`中的第一個介面 ID 的基底類別，請指定 `true` ;否則， `false`。  
  
## 備註  
 協助實作 [實作](../windows/implements-structure.md) 結構。  
  
 這個範本會周遊介面清單並將它們當做基底類別和做為啟用 QueryInterface的必要資訊。  
  
## Members  
  
## 繼承階層架構  
 `ImplementsHelper`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/zh-tw/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)