---
title: "ActivationFactory::GetTrustLevel 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory::GetTrustLevel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTrustLevel 方法"
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory::GetTrustLevel 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得目前 ActivationFactory 具現化物件的信任層級。  
  
## 語法  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### 參數  
 `trustLvl`  
 這個作業完成時， ActivationFactory 執行個體化執行階段類別的信任層級。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，判斷提示錯誤散發，並 `trustLvl` 設為完全信任。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ActivationFactory 類別](../windows/activationfactory-class.md)