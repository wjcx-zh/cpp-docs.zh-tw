---
title: "SimpleClassFactory::CreateInstance 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::SimpleClassFactory::CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInstance 方法"
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SimpleClassFactory::CreateInstance 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立指定介面的執行個體。  
  
## 語法  
  
```  
  
STDMETHOD(  
   CreateInstance  
)  
   (_Inout_opt_ IUnknown* pUnkOuter,   
   REFIID riid,   
   _Deref_out_ void** ppvObject);  
```  
  
#### 參數  
 `pUnkOuter`  
 必須是 `nullptr`;否則，傳回值為 CLASS\_E\_NOAGGREGATION。  
  
 SimpleClassFactory 不支援彙總。  如果彙總 \(Aggregation\) 支援，而建立的物件是彙總的一部分， `pUnkOuter` 是指向彙總的控制項 IUnknown 介面。  
  
 `riid`  
 要建立的物件的介面。  
  
 `ppvObject`  
 當這個作業完成時，由 `riid` 參數指定的對物件執行個體的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 備註  
 如果 \_\_WRL\_STRICT 已定義，且如果類別樣板參數指定的基底類別不是衍生自 [RuntimeClass](../windows/runtimeclass-class.md)，或未使用 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值設定，就會判斷錯誤發出，。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [SimpleClassFactory 類別](../windows/simpleclassfactory-class.md)