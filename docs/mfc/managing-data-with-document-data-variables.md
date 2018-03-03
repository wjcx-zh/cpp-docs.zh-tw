---
title: "使用文件資料變數管理資料 |Microsoft 文件"
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
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c737557d503ca7e0959d159a0818f1ca78280ea2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="managing-data-with-document-data-variables"></a>使用文件資料變數管理資料
實作您的文件資料做為文件類別的成員變數。 例如，Scribble 程式會宣告型別的資料成員`CObList`— 將指標儲存至的連結的清單`CObject`物件。 這份清單用來儲存構成手繪線條的點陣列。  
  
 實作您的文件的成員資料的方式取決於應用程式的本質。 若要有助於了解，MFC 還提供一組 「 集合類別 」 — 陣列、 清單和對應 （字典），包括 c + + 範本為基礎的集合，例如封裝各種不同的一般資料類型的類別以及`CString`， `CRect`， `CPoint`， `CSize`，和`CTime`。 如需有關這些類別的詳細資訊，請參閱[類別庫概觀](../mfc/class-library-overview.md)中*MFC 參考*。  
  
 當您定義文件的成員資料時，您通常會將成員函式加入和取得資料的項目並執行其他有用的作業在其上的文件類別。  
  
 您的檢視來存取文件物件使用的文件中，然後再安裝在建立時檢視中檢視的指標。 您可以藉由呼叫擷取檢視的成員函式中的 this 指標`CView`成員函式**GetDocument**。 請確定這個指標轉換成您自己的文件類型。 然後您可以透過指標存取公用文件成員。  
  
 如果頻繁的資料傳輸需要直接存取，或您想要使用的文件類別的非公用成員，您可能想要讓您的檢視類別 （在 c + + 詞彙） 的文件類別的 friend。  
  
## <a name="see-also"></a>請參閱  
 [使用文件](../mfc/using-documents.md)

