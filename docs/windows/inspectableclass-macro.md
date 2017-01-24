---
title: "InspectableClass 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::InspectableClass"
dev_langs: 
  - "C++"
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InspectableClass 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

設定執行階段類別名稱和信任層級。  
  
## 語法  
  
```cpp  
  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
  
```  
  
#### 參數  
 `runtimeClassName`  
 執行階段類別的完整文字名稱。  
  
 `trustLevel`  
 其中一個 [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) 列舉值。  
  
## 備註  
 `InspectableClass` 巨集只能搭配 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 類型。  
  
## 需求  
 **標頭：**implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)