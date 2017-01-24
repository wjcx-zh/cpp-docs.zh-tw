---
title: "建立您自己的起始頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建立起始頁"
  - "自訂起始頁"
  - "自訂起始頁"
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# 建立您自己的起始頁
您可以使用起始頁專案範本或建立空白起始頁，來建立自訂起始頁。  
  
 因為與 Visual Studio 應用程式模型的相依性，所以 XAML 設計工具可能無法以視覺方式完整精確地呈現自訂起始頁。  
  
## 使用專案範本  
 起始頁專案範本會建立本身為 Visual Studio 起始頁完整複本的起始頁專案。 接著，您可以編輯起始頁，以符合您的規格。  
  
#### 使用起始頁專案範本來建立自訂起始頁  
  
1.  從 Visual Studio 組件庫，下載並安裝[起始頁專案範本](http://go.microsoft.com/fwlink/?LinkId=186204)。  
  
    > [!WARNING]
    >  目前，尚未升級 Visual Studio 2010 起始頁專案範本。 如需如何升級此範本的相關資訊，請參閱[如何：升級 Visual Studio 自訂起始頁](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md)。  
  
2.  安裝範本之後，請使用它來建立新的起始頁專案。  
  
3.  在 \[新增專案\] 對話方塊左窗格的 \[已安裝的範本\] 下，依序展開 \[其他專案類型\] 節點和 \[擴充性\]。  
  
4.  在中間窗格中，按一下 \[自訂起始頁\]，並命名您的專案，然後按一下 \[確定\]。  
  
     Visual Studio 會建立本身為 Visual Studio 起始頁完整複本的起始頁專案。  
  
5.  從**方案總管** 中，開啟 **StartPage.xaml**。  
  
6.  編輯 StartPage.xaml。  
  
     按 F5 鍵開啟已安裝自訂起始頁的 Visual Studio 實驗執行個體，以檢視您的工作。  
  
## 建立空白起始頁  
 建立空白起始頁的最簡單方式是使用起始頁專案範本，然後移除內容。  
  
#### 使用起始頁專案範本來建立空白起始頁  
  
1.  使用起始頁專案範本來建立起始頁專案 \(如先前程序中所述\)。  
  
2.  開啟 StartPage.xaml。  
  
3.  移除所有頁面內容，僅保留外部 XML 項目和包含格線 <xref:System.Windows.Controls.Grid> 項目，因此您的 .xaml 檔案會與下列範例類似。  
  
     [!code-xml[BlankStartPage#01](../misc/codesnippet/Xaml/creating-your-own-start-page_1.xaml)]  
  
4.  移除您不想要使用的任何支援檔案。  
  
     您應該保留 .vsix 和 .pkgdef 檔案，以進行部署。  
  
 或者，您可以建立具有 Visual Studio 可辨識之正確標記結構的 XAML 檔案，來建立空白起始頁。 接著，您可以加入標記和程式碼後置以取得所要的外觀和功能。 如需詳細資訊，請參閱[建立自訂起始頁](../Topic/Creating%20a%20Custom%20Start%20Page.md)。  
  
## 測試並套用自訂起始頁  
 除非您確認自訂起始頁未損毀，否則請不要設定主要執行個體來執行它。 測試過自訂起始頁之後，在 Visual Studio 的主要執行個體中重複這個程序的最後三個步驟，以將它套用至您的系統。  
  
#### 測試自訂起始頁  
  
1.  按 F5。  
  
     在已安裝但未選取新起始頁的情況下，開啟 Visual Studio 實驗執行個體。  
  
2.  在 Visual Studio 實驗執行個體中，按一下 \[工具\] 功能表上的 \[選項\]。  
  
3.  在 \[選項\] 對話方塊的 \[環境\] 下，選取 \[啟動\]。 然後，在 \[自訂起始頁\] 清單上，選取您的 .xaml 檔案，然後按一下 \[確定\]。  
  
4.  在 \[檢視\] 功能表上，按一下 \[起始頁\]。  
  
     運作中起始頁隨即顯示。 您必須關閉實驗執行個體，並重新複製任何變更的檔案，然後重新開啟實驗執行個體以查看新的變更。  
  
 將 .vsix 檔案從 bin\\debug 目錄上傳至 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847)網站，或上傳至另一個網站或內部網路共用，即可共用自訂起始頁。 如需詳細資訊，請參閱[部署自訂起始頁](../Topic/Deploying%20Custom%20Start%20Pages.md)。  
  
## 請參閱  
 [自訂起始頁](../Topic/Customizing%20the%20Start%20Page%20for%20Visual%20Studio.md)   
 [逐步解說: 將自訂的 XAML 加入至 \[開始\] 頁面](../Topic/Walkthrough:%20Adding%20Custom%20XAML%20to%20the%20Start%20Page.md)