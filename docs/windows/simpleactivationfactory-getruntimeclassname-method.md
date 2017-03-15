---
title: "SimpleActivationFactory::GetRuntimeClassName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName"
dev_langs: 
  - "C++"
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleActivationFactory::GetRuntimeClassName 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得由 `Base` 類別樣板參數所指定的類別的執行個體的執行階段類別名稱。  
  
## 語法  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### 參數  
 `runtimeName`  
 這個作業完成時，執行階段類別名稱。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 備註  
 如果 \_\_WRL\_STRICT 已定義，且如果 `Base` 類別樣板參數指定的類別不是衍生自 [RuntimeClass](../windows/runtimeclass-class.md)，或未使用 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值設定，即會判斷錯誤發出。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [SimpleActivationFactory 類別](../windows/simpleactivationfactory-class.md)