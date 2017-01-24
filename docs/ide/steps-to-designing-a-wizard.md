---
title: "設計精靈步驟 | Microsoft Docs"
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
  - "自訂精靈, 設計"
ms.assetid: dc22746b-99e3-4569-a8b4-b3d7cbabf8f2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 設計精靈步驟
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可使用精靈來建立和設定通用專案的起始檔案。  如同任何專案一樣，建立精靈必須詳加規劃。  下列步驟說明一種讓您熟悉 Visual C\+\+ 自訂精靈並將它套用到您自己專案的方法。  
  
1.  檢查 Visual Studio 內附的[自訂精靈範例](http://msdn.microsoft.com/zh-tw/6afa2143-062c-4a68-81ca-66cbf4b95261)。  
  
2.  建立精靈應打好之專案類型的基礎。  如同所有應用建構一樣，這項程序可能經過許多處理和許多不同的重複。  
  
3.  使用 Visual C\+\+ [自訂精靈](../ide/creating-a-custom-wizard.md)來建立專案，指定使用者介面和頁數選項。  
  
    > [!NOTE]
    >  如果您指出使用者介面 \(亦即，如果您清除自訂精靈中在[自訂精靈、應用程式設定](../ide/application-settings-custom-wizard.md)內的 \[使用者介面\]\)，則您的精靈會設定自訂參數 WIZARD\_UI\=**FALSE**，並建立沒有使用者輸入和 .htm 檔的專案樣板檔案。  因此，您並未指定頁數。  如需詳細資訊，請參閱 [.vsz 檔案 \(專案控制\)](../ide/dot-vsz-file-project-control.md)。  
  
4.  檢查自訂精靈為您建立的[基本專案](../ide/examining-the-basic-wizard-project.md)。  
  
5.  如果您的精靈具有使用者介面，請執行精靈來[進一步瞭解自訂精靈的結構](../ide/examining-the-mechanics-of-a-wizard.md)。  
  
6.  [自訂基本精靈](../ide/customizing-your-wizard.md)。  
  
7.  [新增即時線上說明](../ide/providing-context-sensitive-help.md)。  
  
8.  提供 JScript 和 HTML 程式碼的[錯誤處理](../ide/handling-errors-in-wizards.md)。  
  
9. 建置 \(Build\) 和測試精靈。  
  
10. 偵錯您的精靈。  如需詳細資訊，請參閱[偵錯指令碼和 Web 應用程式](../Topic/Debugging%20Web%20Applications%20and%20Script.md)。  
  
    > [!NOTE]
    >  您不可以在偵錯 JScript 時對機器碼執行混合模式偵錯。  
  
## 請參閱  
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)