---
title: "判斷提示和使用者提供的訊息 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3465202908cb0ca375ab5dcc77a085b208071f3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="assertion-and-user-supplied-messages-c"></a>判斷提示和使用者提供的訊息 (C++)
C + + 語言支援三種錯誤處理機制可協助您偵錯應用程式： [#error 指示詞](../preprocessor/hash-error-directive-c-cpp.md)、 [static_assert](../cpp/static-assert.md)關鍵字，而[assert 巨集、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)巨集。 這三種機制都會發出錯誤訊息，其中兩種還會測試軟體判斷提示。 軟體判斷提示會指定您希望在程式中的某個特定點為 true 的條件。 如果編譯時期判斷提示失敗，編譯器會發出診斷訊息和編譯錯誤。 如果執行階段判斷提示失敗，作業系統會發出診斷訊息並關閉應用程式。  
  
## <a name="remarks"></a>備註  
 應用程式的存留期包括前置處理、編譯和執行階段。 每種錯誤處理機制均會存取其中任一階段可用的偵錯資訊。 若要有效偵錯，請選取能夠針對該階段提供適當資訊的機制：  
  
-   [#Error 指示詞](../preprocessor/hash-error-directive-c-cpp.md)即前置處理階段會生效。 它會無條件發出使用者指定的訊息，並且會使編譯失敗並產生錯誤。 訊息可以包含由前置處理器指示詞操作但不會評估任何結果運算式的文字。  
  
-   [Static_assert](../cpp/static-assert.md)宣告是在編譯時期的作用中。 它會測試由使用者指定的整數運算式代表的軟體判斷提示，此判斷提示可以轉換為布林值。 如果運算式判斷值為零 (false)，編譯器會發出使用者指定的訊息，且編譯會失敗並產生錯誤。  
  
     `static_assert` 宣告適用於進行樣板偵錯，因為樣板引數可以包含在使用者指定的運算式中。  
  
-   [Assert 巨集、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)巨集是在執行階段的作用中。 它會評估使用者指定的運算式，如果結果為零，系統會發出診斷訊息並關閉應用程式。 許多其他的巨集，例如[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)和`_ASSERTE`，類似這個巨集，但發出不同系統定義或使用者定義的診斷訊息。  
  
## <a name="see-also"></a>請參閱  
 [#error 指示詞 （C/c + +）](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert 巨集、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT、_ASSERTE、_ASSERT_EXPR 巨集](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_STATIC_ASSERT 巨集](../c-runtime-library/reference/static-assert-macro.md)   
 [範本](../cpp/templates-cpp.md)