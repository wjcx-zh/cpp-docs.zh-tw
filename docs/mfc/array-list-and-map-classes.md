---
title: "陣列、清單和對應類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "陣列 [C++], 類別"
  - "集合類別, 清單"
  - "集合類別, 對應"
  - "清單類別"
  - "對應類別"
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 陣列、清單和對應類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於處理資料彙總，類別庫的集合類別 \(例如陣列、可保留各種物件而預先定義的型別清單和對應的群組中。  設定動態調整大小。  這些類別可以在任何程式，在為視窗。  但是，讓實作器定義在應用程式架構的資料類別的資料結構是最有用的。  您可以從這些立即取得特定的集合類別，或者您可以在根據樣板類別。  如需這些方法的詳細資訊，請參閱本文件的 [集合](../mfc/collections.md)。  如需範本集合類別清單，請參閱本文件的 [陣列、清單和對應的樣板類別](../mfc/template-classes-for-arrays-lists-and-maps.md)。  
  
 陣列是記憶體中連續儲存項目的資料結構。  它們支援非常快速的隨機存取，因為任何特定項目記憶體位址可以藉由將這個項目的索引以項目的大小和將會計算結果到陣列的基底位址 \(Base Address\)。  但是，陣列是非常耗費資源的，如果您必須將元素插入陣列，，因為您可以插入項目的整個陣列必須移動足夠空間可插入的項目。  陣列可以視需要放大和縮小。  
  
 清單類似陣列，但是非常不同方式儲存。  清單中的每個項目也包含指標到前一個和下一個項目，讓雙向連結串列。  因為這樣做只涉及變更指標的陣列，它非常快速地為加入或刪除項目。  不過，，因為所有搜尋需要開始清單結尾，搜尋清單可能會耗用相當多的資源。  
  
 對應的資料值關聯一個關鍵值。  例如，對應的索引鍵可以是字串、游標的清單。  您會要求對應至您指標與特定字串。  因為對應為索引鍵查閱，雜湊資料表對應搜尋很短。  加入和刪除項目也很短。  對應通常與其他資料結構做為額外的索引。  MFC 使用對應呼叫 [訊息對應](../mfc/mapping-messages.md) 的特殊將 Windows 訊息至指標到該訊息的處理函式。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)