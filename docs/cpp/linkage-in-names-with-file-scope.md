---
title: "檔案範圍的名稱連結 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宣告 [C++], 外部"
  - "外部連結, 範圍連結規則"
  - "檔案範圍 [C++]"
  - "連結 [C++], 範圍連結規則"
  - "名稱 [C++], 範圍連結規則"
  - "範圍 [C++], 連結規則"
  - "static 修飾詞, 檔案範圍"
  - "靜態名稱和檔案範圍"
  - "靜態變數, 外部宣告"
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 檔案範圍的名稱連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列連結規則適用於具有檔案範圍的名稱 \(除了 `typedef` 和列舉程式名稱以外\)：  
  
-   如果名稱明確宣告為 **static**，則會具有內部連結，並且會識別本身所屬轉譯單位內的程式項目。  
  
-   列舉程式名稱和 `typedef` 名稱沒有連結。  
  
-   具有檔案範圍的所有其他名稱都具有外部連結。  
  
 **Microsoft 特定的**  
  
-   如果具有檔案範圍的函式名稱明確宣告為 **inline**，則會具有外部連結 \(如果該名稱已具現化，或其位址已做為參考\)。  因此，具有檔案範圍的函式可以有內部或外部連結。  
  
 **END Microsoft 特定的**  
  
 若下列條件成立，類別會有內部連結：  
  
-   類別使用 C\+\+ 功能 \(例如，成員存取控制、成員函式、建構函式、解構函式等\)。  
  
-   類別未在具有外部連結的另一個名稱宣告中使用。  這個條件約束表示，若將類別類型的物件傳遞至具有外部連結的函式，會造成類別擁有外部連結。  
  
## 請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)