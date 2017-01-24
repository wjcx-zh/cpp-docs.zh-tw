---
title: "RemoveReference 結構 | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::RemoveReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RemoveReference 結構"
ms.assetid: 43ff91bb-815a-440e-b9fb-7dcbb7c863af
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RemoveReference 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template<  
   class T  
>  
struct RemoveReference;  
template<  
   class T  
>  
struct RemoveReference<T&>;  
template<  
   class T  
>  
struct RemoveReference<T&&>;  
```  
  
#### 參數  
 `T`  
 類別。  
  
## 備註  
 從指定的類別樣板參數刪除參考或右值參考特性。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Type`|類別樣板參數的同義字。|  
  
## 繼承階層架構  
 `RemoveReference`  
  
## 需求  
 **標題:** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)