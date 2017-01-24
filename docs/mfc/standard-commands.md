---
title: "標準命令 | Microsoft Docs"
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
  - "命令 ID, 標準命令"
  - "命令 [C++], 標準"
  - "編輯功能表標準命令"
  - "檔案功能表"
  - "說明, 功能表"
  - "識別項 [C++], 命令 ID"
  - "OLE 命令"
  - "程式設計人員定義的 ID [C++]"
  - "標準命令 ID"
  - "標準命令"
  - "檢視功能表命令"
  - "視窗功能表命令"
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 標準命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架定義許多標準命令訊息。  這些命令的 ID 通常會採用下列格式:  
  
 **ID\_** *Source*\_*Item*  
  
 其中 *來源* 通常功能表名稱和 *項目* 是功能表項目。  例如，新命令的命令 ID 在檔案功能表是 `ID_FILE_NEW`。  標準命令 ID 在顯示粗體文件。  程式設計人員定義的 ID 會以周圍文字不同的字型顯示。  
  
 下列是支援的某些清單最重要的命令:  
  
 *檔案功能表命令*  
 新增，開啟，關閉，儲存，儲存，版面設定、列印設定、列印、列印預覽、匯出和最近使用過的檔案。  
  
 *編輯結構功能表命令*  
 清除，清除所有，複製，剪下，尋找，貼上，迴圈，取代，選取所有，移除，然後再進行。  
  
 *檢視功能表命令*  
 工具列和狀態列  
  
 *視窗功能表命令*  
 新增，安排，串聯，並排顯示水平，並排顯示垂直和分割。  
  
 *說明功能表命令*  
 索引，使用說明和。  
  
 *OLE 命令\(編輯功能表\)*  
 將新的物件，編輯連結，貼上連結，請將特殊和 *typename* 物件 \(動詞命令\)。  
  
 這個框架為這些命令提供各種支援層級。  而其他支援與徹底的實作，某些命令支援，只有在定義的命令 ID。  例如，此架構會建立新的資料物件，顯示一個開啟對話方塊並開啟和讀取檔案實作檔案功能表上的開啟命令。  相反地，您必須實作編輯功能表上的命令，因為像 **ID\_EDIT\_COPY** 的順序來決定要複製資料的性質。  
  
 如需命令支援的和實作的詳細資訊提供的層級，請參閱 [Technical Note 22](../mfc/tn022-standard-commands-implementation.md)。  標準命令在檔案 AFXRES.H. 定義。  
  
## 請參閱  
 [使用者介面物件和命令 ID](../mfc/user-interface-objects-and-command-ids.md)