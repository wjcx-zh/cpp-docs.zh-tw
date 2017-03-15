---
title: "DontUseNewUseMake::operator new 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator new 運算子"
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# DontUseNewUseMake::operator new 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
void* operator new(  
   size_t,  
   _In_ void* placement  
);  
```  
  
#### 參數  
 `__unnamed0`  
 指定要配置的記憶體位元組數的未命名參數。  
  
 `placement`  
 要配置的型別。  
  
## 傳回值  
 如果您多載運算子 `new`，可提供您一個傳遞其他引數的方式。  
  
## 備註  
 多載運算子 `new` 並防止它在 RuntimeClass 中被使用。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [DontUseNewUseMake 類別](../windows/dontusenewusemake-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)