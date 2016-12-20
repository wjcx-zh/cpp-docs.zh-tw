---
title: "EnableIf 結構 | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::EnableIf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EnableIf 結構"
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EnableIf 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   bool b,  
   typename T = void  
>  
  
struct EnableIf;  
template <  
   typename T  
>  
struct EnableIf<true, T>;  
```  
  
#### 參數  
 `T`  
 類型。  
  
 `b`  
 為布林 \(Boolean\) 運算式。  
  
## 備註  
 如果第一個範本參數評估為 `true`，將第二個定義樣板參數所指定型別的資料成員。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`type`|如果樣板參數 `b` 評估為`true`，部分特製化定義資料成員 `type` 是型別 `T`。|  
  
## 繼承階層架構  
 `EnableIf`  
  
## 需求  
 **標題:** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)