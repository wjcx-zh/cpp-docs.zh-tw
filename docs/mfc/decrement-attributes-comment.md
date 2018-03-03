---
title: "-屬性註解 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- comments, Attributes
- Attributes comment in MFC source files
- MFC source files, Attributes comment
- public attributes comment
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 18a142cc0434e0e09e69d9bffc30826c461cf185
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="-attributes-comment"></a>// 屬性註解
MFC 類別宣告的 `// Attributes` 區段包含物件的公用屬性。 通常這些屬性是成員變數，或是 Get/Set 函式。 「Get」和「Set」函式不一定是虛擬的。 「 Get 」 函式通常是**const**，因為在大部分情況下沒有副作用。 這些成員通常是公用、受保護的私用屬性，一般會在實作區段中。  
  
 中的範例清單裡類別`CStdioFile`下[註解的範例](../mfc/an-example-of-the-comments.md)，此清單包含一個成員變數， `m_pStream`。 `CDC` 類別幾乎列出此註解下的 20 個成員。  
  
> [!NOTE]
>  大型類別 (例如 `CDC` 和 `CWnd`) 可能有許多成員在單一群組中列出所有屬性，但是不會很清楚。 在這種情況下，類別庫會使用其他註解作為標題，進一步描述成員。 例如，`CDC` 會使用 `// Device-Context Functions`、`// Drawing Tool Functions`、`// Drawing Attribute Functions` 等等。 表示屬性的群組會遵循上述的一般語法。 許多 OLE 類別都有稱為 `// Interface Maps` 的實作區段。  
  
## <a name="see-also"></a>請參閱  
 [使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)   
 [註解的範例](../mfc/an-example-of-the-comments.md)   
 [實作註解](../mfc/decrement-implementation-comment.md)   
 [建構函式註解](../mfc/decrement-constructors-comment.md)   
 [作業註解](../mfc/decrement-operations-comment.md)   
 [可覆寫註解](../mfc/decrement-overridables-comment.md)

