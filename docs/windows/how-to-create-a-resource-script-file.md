---
title: "How to: Create a Resource Script File | Microsoft Docs"
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
  - "rc files, creating"
  - ".rc files, creating"
  - "resource script files, creating"
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Create a Resource Script File
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  資源編輯器在 Express 版中無法使用。  
>   
>  這份資料適用於 Windows 桌面應用程式。 以 .NET 語言撰寫的專案不會使用資源指令碼檔。 如需詳細資訊，請參閱[資源檔](../mfc/resource-files-visual-studio.md)。  
  
### 建立新的資源指令碼 \(.rc\) 檔  
  
1.  將焦點放在`Solution Explorer`中的現有專案資料夾中，例如 "MyProject"。  
  
    > [!NOTE]
    >  請勿混淆方案總管中的專案資料夾與方案資料夾。 如果您將焦點放在方案資料夾中，您在 \[加入新項目\] 對話方塊 \(步驟 3\) 中的選擇將會不同。  
  
2.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
3.  在 \[加入新項目\] 對話方塊中，按一下 \[Visual C\+\+\] 資料夾，然後選擇右窗格中的 \[資源檔 \(.rc\)\]。  
  
4.  在 \[名稱\] 文字方塊中提供資源指令碼檔的名稱，然後按一下 \[開啟\]。  
  
 您現在可以[建立](../windows/how-to-create-a-resource.md)新的資源並加入 .rc 檔中。  
  
> [!NOTE]
>  您只能將資源指令碼 \(.rc 檔\) 加入已載入 Visual Studio IDE 的現有專案中， 而不能建立獨立的 .rc 檔 \(即專案以外的檔案\)。[資源範本](../windows/how-to-use-resource-templates.md) \(.rct 檔\) 則可以隨時建立。  
  
 RRequirements  
  
 Win32  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)