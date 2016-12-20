---
title: "類別範圍的名稱連結 | Microsoft Docs"
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
  - "類別名稱 [C++], 連結"
  - "類別範圍 [C++], 名稱連結具有"
  - "類別 [C++], 名稱"
  - "類別 [C++], 範圍"
  - "外部連結, 範圍連結規則"
  - "連結 [C++], 範圍連結規則"
  - "名稱 [C++], 範圍連結規則"
  - "範圍 [C++], 類別名稱"
  - "範圍 [C++], 連結規則"
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類別範圍的名稱連結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列連結規則適用於具有類別範圍的名稱：  
  
-   靜態類別成員具有外部連結。  
  
-   類別成員函式具有外部連結。  
  
-   列舉程式和 `typedef` 名稱沒有連結。  
  
 **Microsoft 特定的**  
  
-   宣告為 `friend` 函式的函式必須具有外部連結。  將靜態函式宣告為 `friend` 會產生錯誤。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [程式和連結](../cpp/program-and-linkage-cpp.md)