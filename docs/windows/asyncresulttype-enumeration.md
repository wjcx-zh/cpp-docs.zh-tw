---
title: "AsyncResultType 列舉 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncResultType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncResultType 列舉"
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncResultType 列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 GetResults \(\) 方法傳回之結果的型別。  
  
## 語法  
  
```  
enum AsyncResultType;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`MultipleResults`|一組在啟動狀態之間與在呼叫 Close\(\) 之前逐步呈獻出來的多個結果。|  
|`SingleResult`|單一結果，在完整事件發生之後呈獻。|  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)