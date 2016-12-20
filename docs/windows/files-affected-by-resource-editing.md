---
title: "Files Affected by Resource Editing | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "resource editing"
  - "resources [Visual Studio], editing"
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Files Affected by Resource Editing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual Studio 環境會在您的資源編輯工作階段期間使用下表中顯示的檔案。  
  
|檔案名稱|描述|  
|----------|--------|  
|偵錯工具|開發環境所產生的標頭檔；包含符號定義。|  
|Filename.aps|目前資源指令碼檔的二進位版本；用於快速載入。<br /><br /> 資源編輯器不會直接讀取.rc 或 resource.h 檔。  資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。  此檔案是一個編譯步驟，只會儲存符號資料。  如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 \(例如註解\)。  每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 \(例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔\)。  資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。  如需註解保留方式的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。|  
|.rc|包含目前專案中的資源所適用之指令碼的資源指令碼檔。  .aps 檔會在您每次存檔時覆寫此檔案。|  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)