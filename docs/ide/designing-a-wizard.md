---
title: "設計精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自訂精靈 [C++], 專案設計"
  - "專案 [C++], 自訂精靈"
  - "Visual C++ 專案, 自訂精靈"
  - "精靈 [C++], 自訂"
ms.assetid: a7c0be7e-9297-4fed-83e3-5645c896d56b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 設計精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可能必須使用與 Visual C\+\+ 中提供的應用程式精靈不同的標準化功能來建立專案。  以這種工作而言，您可使用 Visual C\+\+ 精靈架構，該架構是針對輕易的擴充和自訂功能而設計。  您可使用 [Visual C\+\+ 自訂精靈](../ide/creating-a-custom-wizard.md)來建立精靈。  在建立精靈之後，您可加以設定，來產生專案所需的起始檔案 \(Starter File\)。  
  
 Visual C\+\+ 精靈是一個 HTML 控制項。  它使用 Visual C\+\+ 精靈引擎 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>，它所提供的通用服務有 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI.NavigateToCommandHandler%2A>、<xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI.OkCancelAlert%2A> 等等。  此精靈也會使用指令碼引擎，它可以讓精靈瞭解 VBScript 和 [JScript .NET](http://msdn.microsoft.com/zh-tw/c7e636ee-c10f-45b1-85ec-fe2daca30bf5)。  
  
 此精靈架構可讓您在精靈中直接存取下列物件模型 \(Object Model\)，以及從 JScript 或 HTML 檔案呼叫其方法、屬性和事件  \(如需詳細資訊，請參閱 [HTML 檔案](../ide/html-files.md)和 [JScript 檔案](../ide/jscript-file.md)中的範例\)。  
  
-   [開發者工具環境 \(DTE\) 物件模型](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)  
  
-   [Visual C\+\+ 程式碼模型](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b)  
  
-   [Visual C\+\+ 專案模型](http://msdn.microsoft.com/zh-tw/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)  
  
-   [Visual C\+\+ 精靈模型](http://msdn.microsoft.com/zh-tw/159395ac-33c7-47bf-ad42-4e1435ddc758)  
  
 如需設計精靈之各項目說明的詳細資訊，請參閱[您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)。  
  
## 請參閱  
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈步驟](../ide/steps-to-designing-a-wizard.md)   
 [自訂精靈](../ide/customizing-your-wizard.md)