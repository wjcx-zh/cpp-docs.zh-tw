---
title: "_variant_t 擷取器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t.operatordouble"
  - "operatorlong"
  - "_variant_t::operator_bstr_t"
  - "operatordouble"
  - "_variant_t.operatorCY"
  - "operatorCY"
  - "_variant_t::operatorCY"
  - "_variant_t::operatordouble"
  - "operatorfloat"
  - "operatorBYTE"
  - "_variant_t.operatorDECIMAL"
  - "_variant_t::operatorlong"
  - "operatorIDispatch"
  - "_variant_t.operatorBYTE"
  - "operatorDECIMAL"
  - "_variant_t.operator_bstr_t"
  - "_variant_t::operatorDECIMAL"
  - "_variant_t.operatorIUnknown"
  - "_variant_t.operatorlong"
  - "_variant_t::operatorIDispatch"
  - "_variant_t::operatorIUnknown"
  - "operatorIUnknown"
  - "_variant_t.operatorbool"
  - "_variant_t::operatorBYTE"
  - "_variant_t.operatorfloat"
  - "operator_bstr_t"
  - "_variant_t::operatorbool"
  - "operatorshort"
  - "_variant_t::operatorshort"
  - "_variant_t::operatorfloat"
  - "_variant_t.operatorIDispatch"
  - "_variant_t.operatorshort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "擷取器, _variant_t 類別"
  - "運算子 _bstr_t"
  - "運算子 bool"
  - "運算子 BYTE"
  - "運算子 CY"
  - "運算子 DECIMAL"
  - "運算子 double"
  - "運算子 float"
  - "運算子 IDispatch"
  - "運算子 IUnknown"
  - "運算子 long"
  - "運算子 SHORT"
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t 擷取器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 從封裝的 **VARIANT** 物件中擷取資料。  
  
## 語法  
  
```  
  
      operator short( ) const;   
operator long( ) const;   
operator float( ) const;   
operator double( ) const;   
operator CY( ) const;   
operator _bstr_t( ) const;   
operator IDispatch*( ) const;   
operator bool( ) const;   
operator IUnknown*( ) const;   
operator DECIMAL( ) const;   
operator BYTE( ) const;  
operator VARIANT() const throw();  
operator char() const;  
operator unsigned short() const;  
operator unsigned long() const;  
operator int() const;  
operator unsigned int() const;  
operator __int64() const;  
operator unsigned __int64() const;  
```  
  
## 備註  
 從封裝的 **VARIANT** 中擷取未經處理資料。  如果 **VARIANT** 還不是適當的類型，則會嘗試使用 **VariantChangeType** 進行轉換，並且在失敗時產生錯誤：  
  
-   **運算子 short\( \)**：擷取 **short** 整數值。  
  
-   **運算子 long\( \)**：擷取 **long** 整數值。  
  
-   **運算子 float\( \)**：擷取 **float** 數值。  
  
-   **運算子 double\( \)**：擷取 **double** 整數值。  
  
-   **運算子 CY\( \)**：擷取 **CY** 物件。  
  
-   **運算子 bool\( \)**：擷取 `bool` 值。  
  
-   **運算子 DECIMAL\( \)**：擷取 **DECIMAL** 值。  
  
-   **運算子 BYTE\( \)**：擷取 **BYTE** 值。  
  
-   **運算子 \_bstr\_t\( \)**：擷取封裝在 `_bstr_t` 物件中的字串。  
  
-   **運算子 IDispatch\*\( \)**：從封裝的 **VARIANT** 擷取分配介面 \(Dispinterface\) 指標。  `AddRef` 會在產生的指標上呼叫，因此您可自行決定是否要呼叫 **Release** 將它釋放。  
  
-   **運算子 IUnknown\*\( \)**：從封裝的 **VARIANT** 擷取 COM 介面指標。  `AddRef` 會在產生的指標上呼叫，因此您可自行決定是否要呼叫 **Release** 將它釋放。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)