---
title: "在 Visual c + + 中處理的例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 622bf0194cbf5c3207d161edefcf7da23238fb85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="exception-handling-in-visual-c"></a>Visual C++ 中的例外狀況處理
例外狀況是可能超出程式控制範圍的錯誤條件，它會使得程式無法繼續沿著其正常執行路徑進行。 即使您的程式正常執行，某些作業 (包括建立物件、檔案輸入/輸出以及其他模組發出的函式呼叫) 仍可能是例外狀況的來源。 穩定的程式碼會預測及處理例外狀況。  
  
 若要偵測單一程式或模組內的邏輯錯誤，請使用判斷提示，而不是例外狀況 (請參閱[使用判斷提示](/visualstudio/debugger/c-cpp-assertions))。  
  
 Visual C++ 支援三種例外狀況處理方式：  
  
-   [C + + 例外狀況處理](../cpp/cpp-exception-handling.md)  
  
     對於大部分 C++ 程式，您應該使用具備類型安全的 C++ 例外狀況處理，以確保在堆疊回溯期間叫用物件解構函式。  
  
-   [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)  
  
     Windows 提供自己的例外狀況機制，稱為 SEH。 不建議在 C++ 或 MFC 程式設計中使用這個機制。 只能在非 MFC C 程式中使用 SEH。  
  
-   [MFC 例外狀況](../mfc/exception-handling-in-mfc.md)  
  
     從 3.0 版開始，MFC 使用了 C++ 例外狀況，但是仍支援舊有的例外狀況處理巨集，其形式類似 C++ 例外狀況。 雖然不建議新的程式設計使用這些巨集，但是仍然支援它們以提供回溯相容性。 在已經使用巨集的程式中，您也可以使用 C++ 例外狀況而不受限制。 在前置處理期間，巨集會評估為 Visual C++ 2.0 版之前 C++ 語言的 Visual C++ 實作中所定義的例外狀況處理關鍵字。 在您開始使用 C++ 例外狀況時，可以保留現有的例外狀況巨集。  
  
 使用[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項指定的例外狀況處理的專案中; 中使用的型別預設值為 c + + 例外狀況處理。 請不要混用錯誤處理機制，例如，不要將 C++ 例外狀況與結構化例外狀況處理混用。 使用 C++ 例外狀況處理可讓您的程式碼更具可攜性，並可讓您處理任何類型的例外狀況。 結構化例外狀況處理的缺點的相關資訊，請參閱[結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)。 如需有關混用 MFC 巨集和 c + + 例外狀況的建議，請參閱[例外狀況： 使用 MFC 巨集和 c + + 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。  
  
 如需 CLR 應用程式中處理例外狀況資訊，請參閱[例外狀況處理](../windows/exception-handling-cpp-component-extensions.md)。  
  
 如需有關在 x64 上處理的例外狀況資訊的處理器，請參閱[例外狀況處理 (x64)](../build/exception-handling-x64.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 語言參考](../cpp/cpp-language-reference.md)