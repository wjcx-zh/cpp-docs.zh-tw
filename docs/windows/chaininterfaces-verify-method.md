---
title: "ChainInterfaces::Verify 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::ChainInterfaces::Verify"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Verify 方法"
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ChainInterfaces::Verify 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

確認範本參數`I0`到`I9`所定義的每個介面從 IUnknown 和 IInspectable 繼承，且`I0`從`I1`繼承到 `I9`。  
  
## 語法  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## 備註  
 如果驗證作業失敗， `static_assert` 發出描述失敗的錯誤訊息。  
  
## 備註  
 需要樣板參數 `I0` 和 `I1` ，且參數 `I2``I9` 是選擇性的。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ChainInterfaces 結構](../windows/chaininterfaces-structure.md)