---
title: "起始頁架構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "起始頁架構"
  - "起始頁 XAML"
ms.assetid: f94afe27-0be3-47d9-8e17-b0fd429017bd
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 起始頁架構
本文件說明的 \[起始頁\] 工具視窗 Visual Studio 中所包含的架構。  若要新增或變更 \[啟動\] 頁面中的項目，而不變更其基礎架構，您可以使用這項資訊。  
  
 Visual Studio 的起始頁是寫在 Windows Presentation Foundation \(WPF\) 可延伸應用程式標記語言 \(XAML\)。  如需有關 XAML 標記的詳細資訊，請參閱[XAML 概觀 \(WPF\)](../Topic/XAML%20Overview%20\(WPF\).md)。  
  
## 網頁結構  
 起始頁組成<xref:System.Windows.Controls.Image>項目和第二個<xref:System.Windows.Controls.Grid>中最高層級的項目`Grid` 項目。  `Image`項目橫跨頂端的 \[工具\] 視窗，並包含 Visual Studio 的標誌。  標誌左邊以下`Grid` 項目會包含新的專案，\[命令\] 按鈕**最近使用的專案** 清單中及區域的起始頁的選項。  右邊`Grid` 項目包含<xref:System.Windows.Controls.TabControl>項目具有**開始**索引標籤上， **指南和資源**索引標籤上，和**最新消息** \] 索引標籤。  中央的資料行定義之間左側及右側之`Grid` 項目，但它沒有內容，並只被當作空格字元。  
  
### 視窗內容  
 工具視窗的背景會以最上層`Grid` 項目。  主要的資料行的寬度定義於此，在`ColumnDefinitions`項目。  商標影像的高度會設定`RowDefinitions`項目。  
  
 資料列定義和資料行定義會儲存在以零起始的陣列。  若要在框格中定位項目，設定`Grid.Column`和`Grid.Row`屬性，使其符合相對應的索引<xref:System.Windows.Controls.ColumnDefinition>和<xref:System.Windows.Controls.RowDefinition>項目。  
  
### 商標影像  
 Visual Studio 的標誌會佔據的最上層方格的第一列 \(`Grid.Row="0"`\) 與`Image`項目。  若要顯示不同的圖像，請指向`Source`屬性的`Image`為不同的圖像檔案的項目。  若要移除的影像，請刪除`Image`項目並設定`height`屬性，相對應的最上層`RowDefinition`項目`0` \(零\)，若要隱藏格線的第一列。  
  
### 左欄  
 左邊的欄位的起始頁由`Grid` 項目，在`Grid.Column="0"`和`Grid.Row="1"`。  這個項目包含三個資料列，裝載的指令按鈕\] 方格中，最近使用的專案\] 方格中，定義和`StackPanel`以顯示 Visual Studio 選項的項目。  
  
 將文件新增至現有的資料列的其中一個，或加入新的資料列定義，您可以新增項目到此格線。  當您定義新的資料列時，請記得要遞增`Grid.Row`出現在 \[新的資料列的任何項目的值。  
  
### 中間欄  
 中間欄空格字元，並包含任何項目。  若要加入的中間欄中的項目，位置在`Grid.Column="1"`和`Grid.Row="1"`。  請確定您調整`Width`的資料行定義，以適應變更的屬性。  
  
### 右欄  
 右欄則包含`Grid`項目，在`Grid.Column="1"`和`Grid.Row="1"`。  方格包含`TabControl`中有三個索引標籤的項目。  
  
 您可以加入，以便將定位點<xref:System.Windows.Controls.TabItem>至索引標籤控制項，如所示的項目[逐步解說: 將自訂的 XAML 加入至 \[開始\] 頁面](../Topic/Walkthrough:%20Adding%20Custom%20XAML%20to%20the%20Start%20Page.md)，或者您可以編輯或移除現有的索引標籤。  索引標籤出現在左邊則是以滑鼠右鍵在使用者介面 \(UI\) 中相同的順序由上到下標記中出現。  
  
 如果您新增項目至右欄格線\] 索引標籤控制項的外面，我們建議您定義新的列或欄格線內部，請確定它出現如預期般運作。  
  
## 請參閱  
 [自訂起始頁](../Topic/Customizing%20the%20Start%20Page%20for%20Visual%20Studio.md)   
 [起始頁最佳做法](../misc/start-page-best-practices.md)   
 [部署自訂起始頁](../Topic/Deploying%20Custom%20Start%20Pages.md)