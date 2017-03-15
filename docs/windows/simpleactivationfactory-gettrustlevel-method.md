---
title: "SimpleActivationFactory::GetTrustLevel 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel"
dev_langs: 
  - "C++"
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleActivationFactory::GetTrustLevel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得 `Base` 類別樣板參數所指定的類別的執行個體的信任層級。  
  
## 語法  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### 參數  
 `trustLvl`  
 這個作業完成時，目前的類別物件的信任層級。  
  
## 傳回值  
 永遠為 S\_OK。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)