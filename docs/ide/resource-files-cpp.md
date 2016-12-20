---
title: "資源檔 (C++) | Microsoft Docs"
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
  - "檔案類型 [C++], 資源檔"
  - "資源檔"
  - "資源 [C++]"
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資源檔 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資源是將資訊提供給使用者的介面項目。  點陣圖、圖示、工具列及游標都是資源。  有些資源可用來執行像是從功能表選取或是在對話方塊中輸入資料的動作。  
  
 如需詳細資訊，請參閱[使用資源](../mfc/working-with-resource-files.md)。  
  
|檔案名稱|目錄位置|方案總管位置|描述|  
|----------|----------|------------|--------|  
|*Projname*.rc|*Projname*|原始程式檔|專案的資源指令碼檔。  根據專案的類型以及為專案選取的支援 \(例如工具列、對話方塊或 HTML\) 而定，資源指令碼檔可包含下列項目：<br /><br /> -   預設功能表定義<br />-   快速鍵和字串資料表<br />-   預設 \[**關於**\] 對話方塊<br />-   其他對話方塊<br />-   圖示檔 \(res\\*Projname*.ico\)<br />-   版本資訊<br />-   點陣圖<br />-   工具列<br />-   HTML 檔<br /><br /> 資源檔包含標準 MFC 資源的 Afxres.rc 檔。|  
|Resource.h|*Projname*|標頭檔|資源標頭檔，包含專案所使用資源的定義。|  
|*Projname*.rc2|*Projname*\\res|原始程式檔|指令碼檔，包含專案使用的其他資源。  您可在專案的 .rc 檔最上方包含 .rc2 檔。<br /><br /> .rc2 檔能夠包含幾個不同專案使用的資源。  您不需要個別為不同專案建立相同的資源，而是將它們放入 .rc2 檔並將 .rc2 檔包含在主 .rc 檔當中。|  
|*Projname*.def|*Projname*|原始程式檔|DLL 專案的模組定義檔。  對控制項來說，它會提供控制項的名稱和描述，以及執行階段堆積 \(Heap\) 的大小。|  
|*Projname*.ico|*Projname*\\res|資源檔|專案或控制項的圖示檔。  這個圖示是在最小化應用程式時出現。  它也用在應用程式的 \[**關於**\] 方塊中。  依預設，MFC 提供 MFC 圖示，而 ATL 提供 ATL 圖示。|  
|*Projname*Doc.ico|*Projname*\\res|資源檔|MFC 專案的圖示檔，包含文件\/檢視架構的支援。|  
|Toolbar.bmp|*Projname*\\res|資源檔|在工具列或調色盤 \(Palette\) 中代表應用程式或控制項的點陣圖檔。  這個點陣圖包含在專案的資源檔當中。  初始工具列和狀態列會在 **CMainFrame** 類別中建構。|  
|ribbon.mfcribbon\-ms|*Projname*\\res|資源檔|資源檔，包含定義功能區中按鈕、控制項和屬性的 XML 程式碼。  如需詳細資訊，請參閱 [功能區設計工具 \(MFC\)](../mfc/ribbon-designer-mfc.md)。|  
  
## 請參閱  
 [為 Visual C\+\+ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)