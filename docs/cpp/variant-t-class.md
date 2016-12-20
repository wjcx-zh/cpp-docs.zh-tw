---
title: "_variant_t 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Variant"
  - "_variant_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_variant_t 類別"
  - "_variant_t 類別, 成員函式"
  - "_variant_t 類別, 運算子"
  - "VARIANT 物件"
  - "VARIANT 物件, COM 封裝"
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 `_variant_t` 物件封裝 `VARIANT` 資料類型。  這個類別處理資源配置和解除配置，並對 **VariantInit** 和 **VariantClear** 進行適當的函示呼叫。  
  
### 建構  
  
|||  
|-|-|  
|[\_variant\_t](../cpp/variant-t-variant-t.md)|建構 `_variant_t` 物件。|  
  
### 作業  
  
|||  
|-|-|  
|[附加](../cpp/variant-t-attach.md)|將**VARIANT** 物件附加至 `_variant_t` 物件。|  
|[Clear](../cpp/variant-t-clear.md)|清除封裝的 **VARIANT** 物件。|  
|[ChangeType](../cpp/variant-t-changetype.md)|變更 `_variant_t` 物件的型別至指定的 **VARTYPE**。|  
|[Detach](../cpp/variant-t-detach.md)|自 `_variant_t` 物件中斷封裝的 **VARIANT** 物件。|  
|[SetString](../cpp/variant-t-setstring.md)|指派字串至這個 `_variant_t` 物件。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \=](../cpp/variant-t-operator-equal.md)|將新值指派給現有的 `_variant_t` 物件。|  
|[運算子 \=\= 及 \!\=](../cpp/variant-t-relational-operators.md)|比較兩個 `_variant_t` 物件相等或不相等。|  
|[擷取器（Extractors）](../cpp/variant-t-extractors.md)|從封裝 **VARIANT** 物件擷取資料。|  
  
## END Microsoft 專有  
  
## 需求  
 **標頭：**comutil.h  
  
 **Lib:** comsuppw.lib or comsuppwd.lib \(如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)\)  
  
## 請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)