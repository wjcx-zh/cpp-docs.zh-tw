---
title: "RuntimeClassBaseT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT"
dev_langs: 
  - "C++"
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# RuntimeClassBaseT 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   unsigned int RuntimeClassTypeT  
>  
friend struct Details::RuntimeClassBaseT;  
```  
  
#### 參數  
 `RuntimeClassTypeT`  
 指定一或多個 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值旗標的欄位。  
  
## 備註  
 提供 `QueryInterface` 作業和取得介面 ID 的 Helper 方法。  
  
## Members  
  
## 繼承階層架構  
 `RuntimeClassBaseT`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/zh-tw/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)