---
title: "RuntimeClassFlags 結構 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClassFlags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClassFlags 結構"
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassFlags 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 [RuntimeClass](../windows/runtimeclass-class.md)之執行個體的型別。  
  
## 語法  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### 參數  
 `flags`  
 [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md) 值。  
  
## Members  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[RuntimeClassFlags::value 常數](../windows/runtimeclassflags-value-constant.md)|包含 [RuntimeClassType 列舉](../windows/runtimeclasstype-enumeration.md) 值。|  
  
## 繼承階層架構  
 `RuntimeClassFlags`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)