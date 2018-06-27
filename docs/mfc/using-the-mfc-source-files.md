---
title: 使用 MFC 原始程式檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69079e6f74743a82aa9e9b9b1c13703e480c904c
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951536"
---
# <a name="using-the-mfc-source-files"></a>使用 MFC 原始程式檔
MFC 程式庫提供完整的原始程式碼。 標頭檔 (.h) 位於 \atlmfc\include 目錄中，實作檔 (.cpp) 位於 \atlmfc\src\mfc 目錄。  
  
 這一系列的文章將說明 MFC 用來註解每個類別各部分的慣例、這些註解的方法，以及您在每一個區段中預期應該找到的內容。 Visual C++ 精靈針對將為您建立的類別使用類似的慣例，因此，您可能會發現這些慣例有助於您的程式碼。  
  
 您可能已經熟悉**公用**，**保護**，和**私人**c + + 關鍵字。 當查看 MFC 標頭檔時，您會發現每個類別可能都會出現這些關鍵字。 比方說，公用成員變數和函式可能會顯示在多個**公用**關鍵字。 這是因為，MFC 會根據其使用情形分隔成員變數和函式，而不是依據允許存取的類型分隔。 MFC 使用**私人**謹慎使用; 甚至項目視為實作詳細資料通常會受到保護，並且多次是公用。 雖然不鼓勵存取實作細節，但 MFC 將決定權保留給您。  
  
 在 MFC 原始程式檔和 MFC 應用程式精靈建立的檔案中，您會在類別宣告內發現這類的註解 (通常會依此順序)：  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 此系列文章中涵蓋的主題：  
  
-   [註解的範例](../mfc/an-example-of-the-comments.md)  
  
-   [/ / 實作註解](../mfc/decrement-implementation-comment.md)  
  
-   [/ / 建構函式註解](../mfc/decrement-constructors-comment.md)  
  
-   [/ / 屬性註解](../mfc/decrement-attributes-comment.md)  
  
-   [/ / 作業註解](../mfc/decrement-operations-comment.md)  
  
-   [/ / 可覆寫註解](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>另請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)

