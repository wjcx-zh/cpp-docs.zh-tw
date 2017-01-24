---
title: "IsBaseOfStrict 結構 | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::IsBaseOfStrict"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsBaseOfStrict 結構"
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IsBaseOfStrict 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### 參數  
 `Base`  
 基底型別。  
  
 `Derived`  
 衍生的型別。  
  
## 備註  
 測試一個型別是否為另一個型別的基底。  
  
 第一個範本測試型別是否是衍生自基底型別，可能會產生 **true** 或 **false**。  第二個範本則測試型別是否衍生自本身，永遠會產生 **false**。  
  
## Members  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[IsBaseOfStrict::value 常數](../windows/isbaseofstrict-value-constant.md)|表示型別是否為另一個類別的基底。|  
  
## 繼承階層架構  
 `IsBaseOfStrict`  
  
## 需求  
 **標題:** internal.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)