---
title: "MFC 桌面應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MFC"
  - "mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別庫, MFC"
  - "程式庫, MFC"
  - "MFC, 關於 MFC"
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
caps.latest.revision: 26
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 桌面應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Foundation Class \(MFC\) 程式庫提供許多 Win32 與 COM 應用程式開發介面的物件導向包裝函式。  雖然這個程式庫可以用來建立非常簡單的桌面應用程式，但還是在您需要開發包含多個控制項的較複雜使用者介面時最有用。  您可以使用 MFC 來建立 Office 樣式使用者介面的應用程式。  
  
 《MFC 參考》涵蓋構成 MFC 程式庫的類別、全域函式、全域變數和巨集。  
  
 每個類別所附的個別階層架構圖表對尋找基底類別會很有用。  《MFC 參考》通常不說明繼承的成員函式或繼承的運算子。  如需這些函式的詳細資訊，請參閱階層架構圖表描繪的基底類別。  
  
 每個類別的文件都包含類別概觀、依分類列出的成員摘要，以及成員函式、多載運算子和資料成員的主題。  
  
 公用和受保護類別成員僅在其是以一般方式使用於應用程式或衍生類別時，才會有文件的相關記載。  如需類別成員的完整清單，請參閱類別標頭檔。  
  
> [!IMPORTANT]
>  MFC 類別及其成員無法用於在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]執行的應用程式。  
>   
>  多位元組字元編碼的 \(MBCS\) MFC 程式庫 \(DLL\) 不再隨附於 Visual Studio，但是可以當做 Visual Studio 附加元件。  如需詳細資訊，請參閱 [MFC MBCS DLL 附加元件](../mfc/mfc-mbcs-dll-add-on.md)。  
  
## 本章節內容  
 [概念](../mfc/mfc-concepts.md)  
 MFC 主題的概念性文章。  
  
 [階層架構圖表](../mfc/hierarchy-chart.md)  
 以視覺化方式詳細列出類別庫中的類別關聯性。  
  
 [類別概觀](../mfc/class-library-overview.md)  
 依據分類列出 MFC 程式庫中的類別。  
  
 [逐步解說](../mfc/walkthroughs-mfc.md)  
 包含逐步解說各種與 MFC 程式庫功能相關聯之工作的文件。  
  
 [技術提示](../mfc/mfc-technical-notes.md)  
 提供 MFC 開發小組所撰寫有關類別庫之特定主題的連結。  
  
 [MFC 自訂](../mfc/customization-for-mfc.md)  
 提供一些自訂您的 MFC 應用程式的秘訣。  
  
 [類別](../mfc/reference/mfc-classes.md)  
 提供 MFC 類別的標頭檔資訊和連結。  
  
 [內部類別](../mfc/reference/internal-classes.md)  
 MFC 內部使用。  為求完整起見，本節會說明這些內部類別，但是它們並不適合直接在您的程式碼中使用。  
  
 [巨集和全域](../mfc/reference/mfc-macros-and-globals.md)  
 提供 MFC 程式庫中巨集與全域函式的連結。  
  
 [結構、樣式、回呼和訊息對應](../mfc/reference/structures-styles-callbacks-and-message-maps.md)  
 提供 MFC 程式庫所使用之結構、樣式、回呼及訊息對應的連結。  
  
 [MFC 精靈和對話方塊](../mfc/reference/mfc-wizards-and-dialog-boxes.md)  
 Visual Studio 中用於建立 MFC 應用程式之功能的指南。  
  
 [Working with Resource Files](../mfc/working-with-resource-files.md)  
 如何使用資源檔來管理靜態使用者介面資料，例如 UI 字串和對話方塊版面配置。  
  
## 相關章節  
 [階層架構圖表分類](../mfc/hierarchy-chart-categories.md)  
 依分類說明 MFC 階層架構圖表。  
  
 [ATL\/MFC Shared Classes](../atl-mfc-shared/atl-mfc-shared-classes.md)  
 提供 MFC 和 ATL 之間共用的類別的連結。  
  
 [MFC 範例](../top/visual-cpp-samples.md)  
 提供示範如何使用 MFC 之範例的連結。  
  
 [Visual C\+\+ Libraries Reference](http://msdn.microsoft.com/zh-tw/fec23c40-10c0-4857-9cdc-33a3b99b30ae)  
 提供 Visual C\+\+ 隨附之各種程式庫的連結，這些程式庫包括 ATL、MFC、OLE DB 樣板、C 執行階段程式庫和 Standard C\+\+ 程式庫。  
  
 [Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)  
 提供使用 Visual Studio 偵錯工具來更正應用程式或預存程序 \(Stored Procedure\) 中邏輯錯誤的連結。  
  
## 請參閱  
 [MFC 和 ATL](../mfc/mfc-and-atl.md)