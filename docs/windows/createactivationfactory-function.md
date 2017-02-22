---
title: "CreateActivationFactory 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreateActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateActivationFactory 函式"
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# CreateActivationFactory 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立會產生指定之類別的執行個體的處理站，其可以在 Windows 執行階段啟動。  
  
## 語法  
  
```cpp  
  
template<typename Factory>  
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(  
      _In_ unsigned int *flags,    
      _In_ const CreatorMap* entry,   
      REFIID riid,   
     _Outptr_ IUnknown **ppFactory) throw();  
  
```  
  
#### 參數  
 `flags`  
 一或多個 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值的組合。  
  
 `entry`  
 包含初始化和登入資訊有關參數 `riid`至 [CreatorMap](../windows/creatormap-structure.md) 的指標。  
  
 `riid`  
 對介面 ID的參考。  
  
 `ppFactory`  
 如果這個作業順利完成時，會啟動 Factory 的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，則為表示錯誤的 HRESULT。  
  
## 備註  
 如果樣板參數 `Factory` 不是從 IClassFactory 介面衍生，將會發出 Assert 錯誤。  
  
## 需求  
 **標題：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)