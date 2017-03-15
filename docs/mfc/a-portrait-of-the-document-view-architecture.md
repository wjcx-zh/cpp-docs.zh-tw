---
title: "文件/檢視架構的簡介 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件/檢視架構"
  - "文件/檢視架構, 關於文件/檢視架構"
  - "文件/檢視架構, 從檢視存取資料"
  - "文件, 從檢視存取資料"
  - "文件, 多重檢視"
  - "文件, 檢視"
  - "輸入, 檢視類別"
  - "多重檢視, 從文件更新"
  - "檢視, 存取文件資料來源"
  - "檢視, 和使用者輸入"
  - "檢視, 更新"
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 文件/檢視架構的簡介
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件和檢視在一般 MFC 應用程式配對。  資料儲存在文件中，不過，檢視有對資料的存取權限。  文件分離檢視的從其顯示分隔資料儲存和維護。  
  
## 說明從檢視資料的存取權  
 這個檢視中存取資料的資料可能會使用 [GetDocument](../Topic/CView::GetDocument.md) 函式，將指標傳回文件，或者藉由檢視類別 C \+\+. `friend` 文件類別。  當準備繪製或操作時，這個檢視會使用其資料存取衍生資料。  
  
 例如，從檢視的 [OnDraw](../Topic/CView::OnDraw.md) 成員函式，檢視使用 **GetDocument** 衍生資料指標。  然後它會使用該指標存取文件中的 `CString` 資料成員。  這個檢視只傳遞字串給 `TextOut` 函式。  使用這個範例要查看程式碼，請參閱 [繪製在檢視](../mfc/drawing-in-a-view.md)。  
  
## 使用者輸入到檢視  
 此檢視也會說明在本身內按一下滑鼠以選取或編輯資料。  同樣可以解譯按鍵當資料輸入或編輯。  假設使用者輸入在處理文字的字串。  這個檢視衍生指標文件並使用指標將新資料加入至文件，在某些資料結構儲存它。  
  
## 更新相同文件的多個檢視。  
 在一個應用程式有相同文件的多個檢視 \(例如在文字編輯器中分隔視窗—檢視第一個階段對文件的新資料。  然後它會呼叫文件中的 [UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) 成員函式，表示文件中所有檢視自行更新，以反映新的資料。  這項同步處理檢視。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [文件\/檢視架構的優點](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [文件\/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)