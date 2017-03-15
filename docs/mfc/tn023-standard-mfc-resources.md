---
title: "TN023：標準 MFC 資源 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.resources"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資源 [MFC]"
  - "標準資源"
  - "TN023"
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# TN023：標準 MFC 資源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個附註說明 MFC 程式庫提供和需要的標準資源。  
  
## 標準資源  
 MFC 提供預先定義資源的兩個類別可讓您在應用程式中使用：裁剪圖片資源和標準架構資源。  
  
 裁剪圖片資源是其他與架構無關的資源，但您有可能會想要將它加入至您應用程式的使用者介面中。  下列裁剪圖片資源在一般 MFC 範例 [CLIPART](../top/visual-cpp-samples.md) 中包含：  
  
-   Common.rc：一個資源的單一檔案包含：  
  
    -   表示各種商務和資料處理工作圖示的大型集合。  
  
    -   許多常見的資料指標 \(也請參閱 Afxres.rc\)。  
  
    -   包含數個工具列按鈕的工具列點陣圖。  
  
    -   Commdlg.dll 使用的點陣圖和圖示資源。  
  
-   Indicate.rc：包含狀態列索引鍵狀態指示器的字串資源，例如 Caps Lock 的「CAP」。  
  
-   Prompts.rc：包含每個預先定義命令的功能表提示字串資源，例如 `ID_FILE_NEW` 的「建立新文件」。  
  
-   Commdlg.rc：包含標準 COMMDLG 對話方塊樣板的 Visual C\+\+ 相容 .rc 檔。  
  
 標準架構資源為架構由內部實作而定具有 AFX 定義的 ID 的資源。  您很少需要變更這些 AFX 定義的資源。  如果您要變更，您應該遵循本主題稍後概述的程序。  
  
 下列架構資源在 MFC \\ include 目錄中：  
  
-   Afxres.rc：框架使用的通用資源。  
  
-   Afxprint.rc：指定的列印資源。  
  
-   Afxolecl.rc：指定的 OLE 用戶端應用程式資源。  
  
-   Afxolev.rc：指定的完整 OLE 伺服器應用程式資源。  
  
## 使用裁剪圖片資源  
  
#### 使用裁剪圖片二進位資源  
  
1.  開啟您的 Visual C\+\+ 應用程式的資源檔。  
  
2.  開啟 Common.rc。  這個檔案包含所有二進位裁剪圖片資源。  因為 Common.rc 檔案編譯，這可能需要一些時間。  
  
3.  當您要拖曳您想要使用的資源從 Common.rc 到您應用程式的資源檔時，請按住 CTRL 鍵。  
  
 若要使用其他裁剪圖片資源，請遵循相同的步驟。  唯一的差異在於您會開啟適當的 .rc 檔而不是 Common.rc。  
  
> [!NOTE]
>  請小心不要不小心永久移動 Common.rc 外面的資源。  如果您按住 CTRL 鍵同時拖曳資源時您將會建立複本。  如果您拖曳時沒有按住 CTRL ，資源會移動。  如果擔心您可能不小心變更 Common.rc 檔案，當詢問您是否儲存 Common.rc 的變更請按一下否。  
  
> [!NOTE]
>  .rc 檔資源有特殊 `TEXTINCLUDE` 資源會避免您不小心在頂端儲存標準 .rc 檔案。  
  
### 自訂標準架構資源  
 在應用程式的資源檔中使用 \#include 命令，標準架構資源通常會被包含進應用程式。  AppWizard 將會產生資源檔。  這個檔案包含適當的標準架構資源， 視您選取的 AppWizard 選項。  藉由變更編譯時期指示詞，您可以檢閱、加入或移除被包含的資源。  若要這樣做，請開啟 \[**資源**\] 功能表並選擇 \[**集合包含**\]。  請參閱「編譯時期指示詞」編輯項目。  例如：  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 最常見的自訂標準架構資源案例為加入或移除額外的列印，OLE 用戶端和 OLE 伺服器支援。  
  
 在某些較罕見的情況下您可能會想要自訂標準架構資源內容的特定應用程式，而不只是加入和刪除整個檔案。  下列步驟顯示如何限制包括的資源：  
  
##### 自訂標準資源檔內容  
  
1.  在 Visual C\+\+ 中開啟資源檔。  
  
2.  使用資源集合包括命令，移除您要自訂的標準 .rc 檔的 `#include` 。  例如，自訂列印預覽工具列，請移除 `#include "afxprint.rc"` 這一行。  
  
3.  開啟 MFC \\INCLUDE適當的標準資源檔  在範例之後稍早的本主題中，適當的檔案是 MFC\\Include\\Aafxprint.rc  
  
4.  從標準.rc檔複製所有資源至您的應用程式資源檔案。  
  
5.  在您的應用程式資源檔中修改標準資源的複本。  
  
> [!NOTE]
>  請勿直接在標準 .rc 檔修改資源。  這麼做會修改資源可用在每個應用程式，而不只是在目前工作的值。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)