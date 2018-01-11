---
title: "編譯器 COM 支援類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_raise_error
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9560b4b3a0623a0e712d5b54d2bbe5de7dbc17e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器 COM 支援](../cpp/compiler-com-support.md)   
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)   
 [C++ 語言參考](../cpp/cpp-language-reference.md)