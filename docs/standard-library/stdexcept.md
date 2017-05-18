---
title: '&lt;stdexcept&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<stdexcept>
- std::<stdexcept>
- <stdexcept>
dev_langs:
- C++
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
caps.latest.revision: 19
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a01f0cf531196d59815eb87f03ee9d8a15574088
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;
定義數個標準類別，用於報告例外狀況。 類別構成的衍生階層全都衍生自 [exception](../standard-library/exception-class.md)，而且類別會包含兩種一般的例外狀況類型：邏輯錯誤和執行階段錯誤。 邏輯錯誤會造成程式設計錯誤。 它們衍生自基底類別 logic_error，也包含：  
  
-   `domain_error`  
  
-   `invalid_argument`  
  
-   `length_error`  
  
-   `out_of_range`  
  
 執行階段錯誤會由於程式庫函式或執行階段系統中的錯誤而造成。 它們衍生自基底類別 runtime_error，也包含：  
  
-   `overflow_error`  
  
-   `range_error`  
  
-   `underflow_error`  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[domain_error 類別](../standard-library/domain-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告網域錯誤。|  
|[invalid_argument 類別](../standard-library/invalid-argument-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告無效的引數。|  
|[length_error 類別](../standard-library/length-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告嘗試產生的物件太長而無法指定。|  
|[logic_error 類別](../standard-library/logic-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告在程式執行前假定可偵測的錯誤，例如邏輯前置條件的違規。|  
|[out_of_range 類別](../standard-library/out-of-range-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告引數超出其有效範圍。|  
|[overflow_error 類別](../standard-library/overflow-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告算術溢位。|  
|[range_error 類別](../standard-library/range-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告報告範圍錯誤。|  
|[runtime_error 類別](../standard-library/runtime-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告僅當程式執行時假定可偵測的錯誤。|  
|[underflow_error 類別](../standard-library/underflow-error-class.md)|此類別可做為擲回之所有例外狀況的基底類別，這些例外狀況報告算術反向溢位。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


