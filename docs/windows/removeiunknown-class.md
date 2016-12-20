---
title: "RemoveIUnknown 類別 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::RemoveIUnknown"
dev_langs: 
  - "C++"
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RemoveIUnknown 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### 參數  
 `T`  
 類別。  
  
## 備註  
 產生與 `IUnknown` 為基礎的型別相等的一個型別，不過有非虛擬 `QueryInterface`、 `AddRef`和 `Release` 成員函式。  
  
 根據預設， COM 方法提供虛擬 `QueryInterface`、 `AddRef`版本和方法。  不過， `ComPtr` 不需要額外負荷虛擬方法。  `RemoveIUnknown` 藉由提供私用，非虛擬 `QueryInterface`、 `AddRef`和 `Release` 方法排除該額外負荷。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|說明|  
|--------|--------|  
|`ReturnType`|使用樣板參數 `T` 是相等的，但型別的一個同義資料表有 IUnknown 虛擬成員。|  
  
## 繼承階層  
 `T`  
  
 `RemoveIUnknown`  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)