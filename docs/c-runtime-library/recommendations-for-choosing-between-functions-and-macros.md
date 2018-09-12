---
title: 在函式和巨集之間選擇的建議 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.functions
dev_langs:
- C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5185b3b39ad74381113bd858f9db20ccddfe0fa8
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752595"
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>在函式和巨集之間選擇的建議
大部分的 Microsoft 執行階段程式庫常式都是編譯或組合函式，但有些常式會實作為巨集。 當標頭檔案同時宣告常式的函式和巨集版本時，巨集定義會有較高的優先權，因為它一律會出現在函式宣告之後。 當您叫用同時實作為函式和巨集的常式時，有兩種方法可以強制編譯器使用函式版本：  
  
-   用括號括住常式的名稱。  
  
    ```C
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   使用 `#undef` 指示詞對巨集定義做出「取消定義」：  
  
    ```C
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
如果您需要在程式庫常式的函式和巨集實作之間做選擇，請考慮下列取捨：  
  
-   **速度與大小**：使用巨集的主要優點，在於它的執行時間較快。 在前置處理期間，每次使用巨集時，該巨集都會於內嵌展開 (由其定義取代)。 不論呼叫函式定義的次數為何，它都只會出現一次。 巨集可能會增加程式碼的大小，但不會有和函式呼叫相關的額外負荷。  
  
-   **函式評估**：函式會針對位址進行評估，而巨集不會。 因此您無法在需要指標的內容中使用巨集名稱。 例如，您可以針對函式宣告指標，但不能針對巨集宣告指標。  
  
-   **類型檢查**：當您宣告函式時，編譯器可以檢查引數類型。 由於您無法宣告巨集，所以編譯器無法檢查巨集的引數類型，雖然它可以檢查傳遞至巨集的引數數目。  
  
## <a name="see-also"></a>請參閱  
[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)