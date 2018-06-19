---
title: 文件檢視架構的優點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45065b38128a2e3239b1fd10ded490fdcbcb3eac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340844"
---
# <a name="advantages-of-the-documentview-architecture"></a>文件/檢視架構的優點
若要使用 MFC 文件/檢視架構的主要優點是結構支援多個檢視的相同文件特別好。 （如果您不需要多個檢視的文件/檢視表的小型負擔增加會過度應用程式中，您可以避免架構。 [文件/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)。)  
  
 假設您的應用程式可讓使用者檢視試算表或圖表格式的數值資料。 使用者可能會想要查看同時這兩個原始資料，請在試算表和圖表所產生的資料。 在個別的框架視窗或分隔窗格內的單一視窗中，您就會顯示這些不同的檢視。 現在假設使用者可以編輯試算表，請參閱中的資料所做的變更立即反映在圖表中。  
  
 在 MFC 中，試算表檢視和圖表檢視會根據從 CView 衍生的不同類別。 這兩個檢視將會與單一文件物件關聯。 文件會將資料儲存 （或可能會在從資料庫取得）。 這兩個檢視存取文件，並顯示它們從其擷取的資料。  
  
 當使用者更新的檢視，檢視物件呼叫其中一個`CDocument::UpdateAllViews`。 該函式會告知所有文件的檢視，並檢視每個更新本身的文件的最新資料。 若要在單一呼叫`UpdateAllViews`同步處理在不同的檢視。  
  
 此案例中很難隔離的資料沒有程式碼檢視中，特別是當檢視儲存的資料本身。 文件/檢視表，很容易。 架構會為您執行大部分的協調工作。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [文件/檢視的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [CDocument](../mfc/reference/cdocument-class.md)  
  
-   [CView](../mfc/reference/cview-class.md)  
  
-   [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)  
  
-   [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)  
  
## <a name="see-also"></a>另請參閱  
 [文件/檢視架構](../mfc/document-view-architecture.md)

