---
title: "DontUseNewUseMake 類別 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::DontUseNewUseMake"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DontUseNewUseMake 類別"
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DontUseNewUseMake 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
class DontUseNewUseMake;  
```  
  
## 備註  
 避免在 RuntimeClass 內使用運算子 `new` 。  因此，您必須使用 [執行函式](../windows/make-function.md) 。  
  
## Members  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[DontUseNewUseMake::operator new 運算子](../windows/dontusenewusemake-operator-new-operator.md)|多載運算子 `new` 並防止它在 RuntimeClass 中被使用。|  
  
## 繼承階層架構  
 `DontUseNewUseMake`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)   
 [Make 函式](../windows/make-function.md)