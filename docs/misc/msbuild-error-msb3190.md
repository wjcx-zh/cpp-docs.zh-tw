---
title: "MSBuild 錯誤 MSB3190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3190
**MSB3190: ClickOnce 不支援所需的執行層級 '\<層級\>'。**  
  
 這是在執行 Windows Vista 的電腦上，當應用程式的內嵌使用者帳戶控制 \(User Account Control，UAC\) 資訊清單指定 ClickOnce 應用程式使用管理認證執行時，產生的錯誤。  ClickOnce 及免註冊的 COM 需要指定應用程式以目前使用者身分執行的外部資訊清單。  
  
 ClickOnce 不接受執行層級 `requireAdministrator` 或 `highestAvailable`。  如果您指定其中一個層級，就會收到錯誤。  ClickOnce 需要 `asInvoker`，但也能接受沒有 `<requestedExecutionLevel>` 節點，指定檔案\/登錄虛擬化 \(表示不會產生資訊清單，這是為了回溯相容而執行的\)。  
  
> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要更正這個錯誤  
  
-   產生一個外部 UAC 資訊清單 \(app.manifest\)，指定應用程式以目前使用者身分 \(`asInvoker`\) 執行。  
  
     在 Visual C\# 專案中，移至 \[專案設計工具\] 的 \[**應用程式**\] 頁面，然後按一下 \[**資訊清單**\] 中的 \[**Properties\\app.manifest**\]。  如需詳細資訊，請參閱[專案設計工具，應用程式頁 \(C\#\)](../Topic/Application%20Page,%20Project%20Designer%20\(C%23\).md)。  
  
     在 Visual Basic 專案中，移至 \[專案設計工具\] 的 \[**應用程式**\] 頁面，然後按一下 \[**檢視 UAC 設定**\] 按鈕，  會開啟 app.manifest 以進行編輯。  編輯資訊清單中的下列標籤，以使其顯示如下：  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     如需詳細資訊，請參閱 [應用程式頁面，專案設計工具 \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)。  
  
-   如需如何產生 UAC 資訊清單及指定執行層級的詳細資訊，請參閱 [Windows Vista 的 ClickOnce 部署](../Topic/ClickOnce%20Deployment%20on%20Windows%20Vista.md)。  
  
## 請參閱  
 [專案設計工具，應用程式頁 \(C\#\)](../Topic/Application%20Page,%20Project%20Designer%20\(C%23\).md)   
 [應用程式頁面，專案設計工具 \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)   
 [Windows Vista 的 ClickOnce 部署](../Topic/ClickOnce%20Deployment%20on%20Windows%20Vista.md)