---
title: "Previewing Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.previewing"
  - "vs.resvw.resource.previewing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "resource previews"
  - "code, viewing"
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Previewing Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

預覽資源可讓您檢視圖形式資源，而不用開啟它們。  預覽功能也可用於編譯後的執行檔上，因為資源識別項已變成數字。  因為這些數值識別項通常未提供足夠的資訊，預覽資源可協助您迅速識別它們。  
  
 您可預覽下列資源類型的視覺配置：  
  
-   點陣圖  
  
-   對話方塊  
  
-   圖示  
  
-   Menu  
  
-   Cursor  
  
-   Toolbar  
  
 對於快速鍵 \(Accelerator\)、資訊清單 \(Manifest\)、字串資料表 \(String Table\) 和版本資訊 \(Version Information\) 資源不適用視覺預覽功能。  
  
### 若要預覽資源  
  
1.  在[資源檢視](../windows/resource-view-window.md)或文件視窗內選取您的資源，例如 IDD\_ABOUTBOX。  
  
     **請注意**：如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)中按一下 \[屬性頁\] 按鈕。  
  
     \-或\-  
  
3.  在 \[**檢視**\] 功能表上按一下 \[**屬性頁**\]。  
  
     該資源的屬性頁將會開啟，顯示該資源的預覽畫面。  接著您可使用向上和向下鍵來巡覽 \[資源檢視\] 或文件視窗中的樹狀控制項。  \[屬性頁\] 將持續開啟，並顯示任何擁有焦點並可預覽的資源。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [How to: Open a Resource Script File Outside of a Project \(Standalone\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Resource Editors](../mfc/resource-editors.md)