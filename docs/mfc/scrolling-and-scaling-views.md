---
title: "捲動和縮放檢視 | Microsoft Docs"
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
  - "訊息處理常式"
  - "訊息處理, 檢視類別中的捲軸"
  - "縮放檢視"
  - "捲軸, 訊息"
  - "捲動檢視"
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 捲動和縮放檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 支援捲動和檢視會自動縮放至框架視窗的大小以顯示其檢視。  `CScrollView` 類別支援兩種檢視。  
  
 如需捲動和縮放的詳細資訊，請參閱《 *MFC 參考》中的*[CScrollView](../mfc/reference/cscrollview-class.md) 類別。  如需捲動範例，請參閱 [Scrum 的範例](../top/visual-cpp-samples.md)。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   捲動檢視  
  
-   檢視。  
  
-   [\<caps:sentence id\="tgt8" sentenceid\="f321fcf7c88bc6e3f892ae0fc9b2f0d8" class\="tgtSentence"\>檢視座標。\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a> 捲動檢視  
 通常文件大小大於其檢視可以顯示的大小。  這可能會發生，因為文件的資料加入或使用者合約框架檢視的視窗。  在這些情況下，檢視必須支援捲動。  
  
 所有檢視可以處理其 `OnHScroll` 和 `OnVScroll` 成員函式的捲動列訊息。  您可以實作捲動列在這些函式的訊息處理，完成所有工作，或是使用 `CScrollView` 類別來管理捲動。  
  
 `CScrollView` 會執行下列各項：  
  
-   處理視窗與檢視區大小和對應模式。  
  
-   自動捲動以回應捲動列訊息  
  
 您可以指定要為「Page」捲動 \(當使用者捲動列軸按一下\) 和「行」\(當使用者捲動箭號指向一下\)。  計劃這些值符合您的檢視而定。  例如，您可能想要移動在圖形檢視中增加 1 個像素，但會根據 Word 文件中的行高的加入。  
  
##  <a name="_core_scaling_a_view"></a> 檢視。  
 當您要檢視自動配合其框架視窗的大小時，您可以為會使用 `CScrollView` 而不是捲動。  邏輯檢視自動縮放或壓縮以完全符合視窗的工作區。  一個稱為的檢視沒有捲軸。  
  
## 請參閱  
 [使用檢視](../mfc/using-views.md)