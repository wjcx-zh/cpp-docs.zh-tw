---
title: "編譯器 COM 支援類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_raise_error
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
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
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 48540910db97e7662eeaa7e8a7febf7e44df653b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="compiler-com-support-classes"></a>編譯器 COM 支援類別
**Microsoft 特定的**  
  
 標準類別用來支援某些 COM 類型。 這些類別是在 comdef.h 中定義，而這些標頭檔是從類型程式庫產生的。  
  
|類別|用途|  
|-----------|-------------|  
|[_bstr_t](../cpp/bstr-t-class.md)|包裝 `BSTR` 類型可提供有用的運算子和方法。|  
|[_com_error](../cpp/com-error-class.md)|定義所擲回的錯誤物件[_com_raise_error](../cpp/com-raise-error.md)中最多失敗。|  
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|封裝 COM 介面指標，以及自動化所需的呼叫`AddRef`，**發行**，和`QueryInterface`。|  
|[_variant_t](../cpp/variant-t-class.md)|包裝**VARIANT**可提供有用的運算子和方法的型別。|  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 支援](../cpp/compiler-com-support.md)   
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)   
 [C++ 語言參考](../cpp/cpp-language-reference.md)
