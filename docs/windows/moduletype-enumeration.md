---
title: "ModuleType 列舉 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ModuleType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ModuleType 列舉"
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ModuleType 列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定模組是否應支援同處理序伺服程式或跨處理序的伺服器。  
  
## 語法  
  
```  
enum ModuleType;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`InProc`|一個處理程序內的伺服器。|  
|`OutOfProc`|跨處理序的伺服器。|  
|`DisableCaching`|停用模組中的快取機制。|  
|`InProcDisableCaching`|`InProc` 和 `DisableCaching` 的組合。|  
|`OutOfProcDisableCaching`|`OutOfProc` 和 `DisableCaching` 的組合。|  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)