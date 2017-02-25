---
title: "一階段和兩階段的物件建構 | Microsoft Docs"
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
  - "建立物件, 圖形物件"
  - "物件 [C++], 建立圖形物件"
  - "物件 [C++], 圖形物件"
  - "一階段和兩階段的物件建構"
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 一階段和兩階段的物件建構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您有兩個建立圖形物件技術的選擇，例如畫筆和筆刷：  
  
-   *一個階段建構*：建構並初始化在一個階段中，皆使用建構函式。  
  
-   *兩個階段建構*：建構並初始化物件兩個不同階段。  建構函式會建立物件及初始化函式將它初始化。  
  
 兩個階段建構永遠比較安全。  在一個階段建構，如果您提供不正確的引述或記憶體配置失敗，建構函釋會值回例外狀況。  該問題由兩階段建構避免，不過您必須檢查失敗。  在任何情況下，終結物件是相同的處理序。  
  
> [!NOTE]
>  這些技術適用於建立所有物件，而不只是圖形物件。  
  
## 兩個建構技術的範例  
 下列簡短範例顯示建構畫筆物件的兩個方法：  
  
 [!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/CPP/one-stage-and-two-stage-construction-of-objects_1.cpp)]  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [圖形物件](../mfc/graphic-objects.md)  
  
-   [選取圖形物件放入裝置內容中](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [裝置內容](../mfc/device-contexts.md)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
## 請參閱  
 [圖形物件](../mfc/graphic-objects.md)