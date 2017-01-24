---
title: "主動式文件內含項目範例：Office 文件夾 | Microsoft Docs"
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
  - "主動式文件容器 [C++], 範例"
  - "主動式文件 [C++], 容器"
  - "容器 [C++], 主動式文件"
  - "範例 [C++], 主動式文件內含項目"
  - "MFC COM [C++], 主動式文件內含項目"
  - "Office 文件夾"
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 主動式文件內含項目範例：Office 文件夾
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Office Binder 是主動式文件容器的範例。  Office 文件夾如一般容器包含兩個主要窗格。  左窗格會包含任何對應於繫結器的現用文件的圖示。  每個文件會呼叫繫結器中的*區段*。  例如，繫結器可以包含Word文件， PowerPoint 檔， Excel 報表等等。  
  
 按一下左窗格中的圖示啟動對應的現用文件。  繫結器的右窗格會顯示目前選取的現用文件的內容。  
  
 如果您開啟並啟動在繫結器中的 Word 文件，文字功能表列和工具列會出現在檢視的頂端，使用所有文字命令或工具，因此，您可以編輯文件的內容。  不過，功能表列是繫結器的和文字的組合功能表列。  由於繫結器和文字有 **Help** 功能表，個別功能表的內容合併。  主動式文件容器 \(例如 Office 文件夾自動提供 **Help** 功能表合併;如需詳細資訊，請參閱 [說明功能表合併](../mfc/help-menu-merging.md)。  
  
 當您選取另一個應用程式類型時現用文件，繫結器的介面變更容納該現用文件的應用程式類型。  例如，如果繫結器包含 Excel 報表，則當您選取 Excel 試算表區段時，您會注意到在繫結器的功能表變更。  
  
 當然也有其他可能容器的型別在繫結器旁邊。  檔案總管使用左窗格使用樹狀目錄控制項顯示在磁碟或網路的目錄的階層式清單的典型的雙重介面，而使用右窗格顯示目前選取目錄中的檔案內。  網際網路瀏覽器型容器 \(例如 Microsoft Internet Explorer\) 使用超連結，而不是使用通常具有單一框架並提供巡覽的雙窗格介面。  
  
## 請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)