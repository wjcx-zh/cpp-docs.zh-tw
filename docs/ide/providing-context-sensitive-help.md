---
title: "提供即時線上說明 | Microsoft Docs"
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
  - "即時線上說明"
  - "即時線上說明, 自訂精靈"
  - "自訂精靈, 實作說明"
ms.assetid: c6c4d961-29d3-4d16-9f39-b12545aba540
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 提供即時線上說明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用[自訂精靈](../ide/application-settings-custom-wizard.md)建立精靈時，它會在您的精靈上插入 \[說明\] 按鈕。  
  
 您專案中的每一個 .htm 檔都包含下列程式碼，為您的精靈提供 \[說明\] 按鈕支援。  
  
```  
<BUTTON CLASS="BUTTONS" ID="HelpBtn" ACCESSKEY="H"  
 onClick="window.external.OnHelp('vc.appwiz.custom.overview');">  
```  
  
 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.OnHelp%2A> 會指定與該精靈頁面關聯的 HTML 說明檔之關鍵字。  如需建立與該頁面關聯之 HTML 說明檔的詳細資訊，請參閱 [HTML 說明起始頁](vsconhh1start)。  若要提供您自己對這個精靈頁面的說明，您必須將 `'vc.appwiz.custom.overview'` 字串取代成可以辨識該頁面的 HTML 說明主題之關鍵字。  
  
 **注意** 這個 .htm 檔無法整合到已完成編譯的 MSDN 說明中。  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/custom-wizard.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)