---
title: "_variant_t 擷取器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
dev_langs:
- C++
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: 9ec02d82529a6772e079305c34c5f43ee163a2f7
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="variantt-extractors"></a>_variant_t 擷取器
**Microsoft 特定的**  
  
 從封裝擷取資料**VARIANT**物件。  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="remarks"></a>備註  
 從封裝中擷取未經處理資料**VARIANT**。 如果**VARIANT**還不適當的類型， **VariantChangeType**使用嘗試進行轉換，而且在失敗時產生的錯誤：  
  
-   **運算子 short （)**擷取**簡短**整數值。  
  
-   **運算子 long （)**擷取**長**整數值。  
  
-   **運算子 float （)**擷取**float**數值。  
  
-   **運算子 double （)**擷取**double**整數值。  
  
-   **運算子 CY （）**擷取**CY**物件。  
  
-   **運算子 bool （)**擷取`bool`值。  
  
-   **運算子 DECIMAL （）**擷取**十進位**值。  
  
-   **運算子 BYTE （）**擷取**位元組**值。  
  
-   **運算子 _bstr_t （)**擷取封裝在字串`_bstr_t`物件。  
  
-   **運算子 IDispatch\*（)**從封裝擷取分配介面指標**VARIANT**。 `AddRef`呼叫產生的指標，所以您必須呼叫**發行**將它釋放。  
  
-   **運算子 IUnknown\*（)**從封裝擷取 COM 介面指標**VARIANT**。 `AddRef`呼叫產生的指標，所以您必須呼叫**發行**將它釋放。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)

