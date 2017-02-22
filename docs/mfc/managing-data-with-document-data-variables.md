---
title: "使用文件資料變數管理資料 | Microsoft Docs"
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
  - "類別 [C++], friend"
  - "集合類別 [C++], 文件物件所使用的"
  - "資料 [MFC]"
  - "資料 [MFC], 文件"
  - "文件資料 [C++]"
  - "文件 [C++], 資料儲存"
  - "friend 類別"
  - "成員變數 [C++], 文件類別"
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用文件資料變數管理資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

實作您的文件中的資料，您的資料成員變數的分類。  例如， Scribble 程式宣告型別 `CObList` —存放指標對 `CObject` 物件的連結串列的資料成員。  這份清單是用來儲存組成徒手繪製掃描線的點陣列。  
  
 如何實作自己的資料成員的資料取決於您應用程式的本質。  協助您， 「設定一組分類」的 MFC 提供—陣列，清單，並將 \(字典\)，包含以 C\+\+ 樣板的集合—與類別一起封裝各種不同通用資料型別 \(例如 `CString`、 `CRect`、 `CPoint`、 `CSize`和 `CTime`。  如需這些類別的詳細資訊，請參閱《 *MFC 參考》中的*[類別庫概觀](../mfc/class-library-overview.md) 。  
  
 當您定義資料成員的資料，您通常會將成員函式到文件類別設定和取得資料項目和執行其他有用的作業。  
  
 您要存取文件物件使用檢視的指標文件，安裝在此檢視中建立時。  您可以藉由呼叫 `CView` 成員函式來擷取在檢視的成員函式中的這個指標 **GetDocument**。  請務必將這個指標到您的資料型別。  然後您可以傳遞指標存取公文書成員。  
  
 如果經常資料傳輸要求直接存取，或者您使用文件的非公用成員的繼續進行分類，您也可以交換檢視類別 friend \(用 C\+\+ 用語\) 文件類別。  
  
## 請參閱  
 [使用文件](../mfc/using-documents.md)