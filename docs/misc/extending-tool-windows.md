---
title: "擴充工具視窗 | Microsoft Docs"
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
  - "視窗 [Visual Studio SDK], 工具"
  - "文件視窗"
  - "工具視窗"
  - "視窗 [Visual Studio SDK], 文件"
ms.assetid: 252f7b99-b44a-4a63-88d9-3a0ca48ac4f1
caps.latest.revision: 37
caps.handback.revision: 37
manager: "douge"
---
# 擴充工具視窗
在一般情況下，Visual Studio 工具視窗為非檔案型的唯讀視窗。 在這種情況下，它們與文件視窗不同，而文件視窗會以讀寫模式顯示檔案。 \[工具箱\]、**方案總管**、\[屬性\] 視窗和 \[網頁瀏覽器\] 是工具視窗範例。  
  
 Visual Studio 2010 和更新版本中的所有工具視窗都是以 WPF 為基礎。 在 Visual Studio 2010 之前的 Visual Studio 版本中，工具視窗是以 Windows Forms 為基礎。 仍然會顯示以 Windows Forms 為基礎的視窗，但新的工具視窗必須是以 WPF 為基礎。  
  
## 工具視窗基本項目  
 若要提供工具視窗，您必須向 Visual Studio 註冊它，並指定其預設大小和位置。 如需詳細資訊，請參閱[在登錄中的工具視窗](../Topic/Tool%20Windows%20in%20the%20Registry.md)。  
  
 按一下功能表命令，通常即會建立或開啟工具視窗。 若要以程式設計方式建立工具視窗，請參閱[以程式設計方式開啟工具視窗](../misc/opening-a-tool-window-programmatically.md)。  
  
 工具視窗預設是單一執行個體，這表示一次只能開啟工具視窗的一個執行個體。 單一執行個體工具視窗在開啟之後，除非關閉 IDE，否則仍然會持續開啟。 當您按一下單一執行個體工具視窗上的 \[關閉\] 按鈕時，只會變更其可見性。 您也可以建立多執行個體工具視窗，這樣即可同時開啟視窗的多個執行個體。 如需詳細資訊，請參閱 [建立多個執行個體工具視窗](../Topic/Creating%20a%20Multi-Instance%20Tool%20Window.md)。  
  
 在文件框架中，可以停駐、浮動或標籤工具視窗。 工具視窗框架是由 IDE 所提供，並可用來控制大小、位置、停駐狀態和其他持續性屬性。 工具視窗窗格會顯示內容。 只有在第一次開啟工具視窗時，才會套用預設大小和位置；之後，就會持續保存工具視窗狀態。  
  
 工具視窗窗格可以裝載 WPF 使用者控制項，並支援工具列。 您可以覆寫 <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 屬性來傳回所裝載控制項的控制代碼。  
  
 工具視窗可以是*「動態」*\(dynamic\) \(也稱為*「自動顯示」*\(auto\-visible\)\)。 只要套用動態工具視窗的相關 UI 內容，就會顯示動態工具視窗。 使用自動顯示可以減少 IDE 中視窗的雜亂。 如需詳細資訊，請參閱[開啟動態工具視窗](../Topic/Opening%20a%20Dynamic%20Tool%20Window.md)。  
  
 VSPackage 不是建立工具視窗的唯一方式。 增益集可以使用 Visual Studio Automation 模型來建立工具視窗。 如需詳細資訊，請參閱[如何：建立並控制工具視窗](../Topic/How%20to:%20Create%20and%20Control%20Tool%20Windows.md)。  
  
## 請參閱  
 [Tool Windows](../misc/extending-tool-windows.md)   
 [文件視窗](../Topic/Document%20Windows.md)   
 [加入搜尋工具視窗](../Topic/Adding%20Search%20to%20a%20Tool%20Window.md)