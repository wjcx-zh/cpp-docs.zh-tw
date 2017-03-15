---
title: "CreateClassFactory 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreateClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateClassFactory 函式"
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# CreateClassFactory 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立會產生指定類別的執行個體的 Factory。  
  
## 語法  
  
```cpp  
  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### 參數  
 `flags`  
 一或多個 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值的組合。  
  
 `entry`  
 包含初始化和登入資訊有關參數 `riid`至 [CreatorMap](../windows/creatormap-structure.md) 的指標。  
  
 `riid`  
 對介面的參考 ID。.  
  
 `ppFactory`  
 如果這個作業成功完成， Class Factory 的指標。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 備註  
 如果樣板參數 `Factory` 不是從 IClassFactory 介面衍生，將會發出 Assert 錯誤。  
  
## 需求  
 **標題：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)