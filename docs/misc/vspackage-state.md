---
title: "VSPackage 狀態 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "狀態, VSPackage"
  - "VSPackage, 管理應用程式狀態"
  - "狀態持續性"
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
caps.handback.revision: 25
manager: "douge"
---
# VSPackage 狀態
受到許多因素永續性的值\] 或 \[狀態中，一組的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]應用程式。  
  
-   專案會有專案\] 和 \[組態屬性。  
  
-   解決方案都有屬性。  
  
-   使用者設定會決定的大小和位置的文件視窗、 工具視窗、 固定的狀態和鍵盤快速鍵。  
  
-   應用程式可以有使用者設定的選項。  
  
-   應用程式建立的物件可以有自己的屬性。  
  
 下面是幾種方法， [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]可以管理應用程式狀態：  
  
-   透過專案\] 和 \[方案屬性頁中。  
  
-   透過**匯入和匯出設定精靈**，可讓使用者能夠設定從某部電腦移到另一個。  
  
-   透過**選項** \] 對話方塊，其中包含與應用程式相關的選項。  
  
-   透過**屬性** \] 視窗中，其會顯示物件的屬性。  
  
-   「 自動化 」。  應用程式可以存取已公開自動化的 VSPackage 和物件的屬性。  
  
 基礎應用程式狀態是不同的保存性機制，可讓應用程式狀態儲存和還原。  
  
## 在本節中  
 [狀態持續性支援](../misc/support-for-state-persistence.md)  
 列出通用的策略，儲存、 還原，及重設 VSPackage 的狀態。  
  
 [選項和選項頁面](../Topic/Options%20and%20Options%20Pages.md)  
 介紹 \[一般\] 及 \[自訂的 \[選項\] 頁，並說明如何實作它們。  
  
 [建立選項\] 頁面](../Topic/Creating%20an%20Options%20Page.md)  
 說明如何建立兩個選項頁\]、 \[簡單的網頁及 \[自訂頁面。  
  
 [設定類別的支援](../misc/support-for-settings-categories.md)  
 討論使用者設定，以及如何建立及保存它們。  
  
 [建立設定分類](../Topic/Creating%20a%20Settings%20Category.md)  
 說明如何建立[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定類別中，並用來儲存值並還原從設定檔的值。  
  
 [擴充屬性和 \[屬性\] 視窗](../Topic/Extending%20Properties%20and%20the%20Property%20Window.md)  
 說明如何顯示及變更的值中物件的**屬性**視窗。  
  
 [公開屬性至屬性視窗](../Topic/Exposing%20Properties%20to%20the%20Properties%20Window.md)  
 說明如何以物件的公用屬性公開 \(expose\) **屬性**視窗。  
  
 [專案和組態屬性的支援](../Topic/Support%20for%20Project%20and%20Configuration%20Properties.md)  
 說明如何顯示，並變更 \[專案\] 和 \[組態屬性。  
  
 [取得專案屬性](../Topic/Getting%20Project%20Properties.md)  
 引導您完成建立受管理的 VSPackage 工具視窗中顯示專案屬性的步驟。  
  
 [使用 「 設定存放區](../Topic/Using%20the%20Settings%20Store.md)  
 說明設定存放區的保存性機制，以及如何使用它。  
  
## 相關章節  
 [Vspackage](../Topic/VSPackages.md)  
 提供主題為說明如何建立及使用 VSPackages 的一般方向。