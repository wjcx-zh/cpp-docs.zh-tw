---
title: "How to: Open a Resource Script File in Text Format | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource script files, opening in text format"
  - ".rc files, opening in text format"
  - "rc files, opening in text format"
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Open a Resource Script File in Text Format
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有時候您會想要檢視專案資源指令碼 \(.rc\) 檔內容，而不想開啟其特定資源編輯器內的資源 \(例如對話方塊\)。  例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。  
  
> [!NOTE]
>  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
 您可以輕鬆地以文字格式開啟資源檔，以檢視其包含的所有資源，並執行[文字編輯器](http://msdn.microsoft.com/zh-tw/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)支援的全域作業。  
  
> [!NOTE]
>  資源編輯器不會直接讀取.rc 或 resource.h 檔。  資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。  此檔案是一個編譯步驟，只會儲存符號資料。  如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 \(例如註解\)。  每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 \(例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔\)。  資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。  如需註解保留方式的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。  
  
### 將資源指令碼檔開啟為文字  
  
1.  從 \[**檔案**\] 功能表，選擇 \[**開啟**\]，然後按一下 \[**檔案**\]。  
  
2.  在 \[**開啟檔案**\] 對話方塊中，導覽至您要以文字格式檢視的資源指令碼檔。  
  
3.  反白顯示檔案，然後按一下 \[**開啟**\] 按鈕上的下拉箭號 \(位於按鈕右邊\)。  
  
4.  從下拉式功能表選擇 \[**開啟方式**\]。  
  
5.  在 \[**開啟方式**\] 對話方塊中，按一下 \[**原始程式碼 \(文字\) 編輯器**\]。  
  
6.  請從 \[**開啟為**\] 下拉式清單中，選取 \[**文字**\]。  
  
     資源隨即在 \[原始程式碼編輯器\] 中開啟。  
  
 \-或\-  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 .rc 檔。  
  
2.  從捷徑功能表，選擇 \[**開啟方式...**\]，然後選取 \[**原始程式碼 \(文字\) 編輯器**\]。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)