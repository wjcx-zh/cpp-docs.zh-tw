---
title: "/MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.UACUIAccess"
  - "VC.Project.VCLinkerTool.UACExecutionLevel"
  - "VC.Project.VCLinkerTool.EnableUAC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTUAC 連結器選項"
  - "MANIFESTUAC 連結器選項"
  - "-MANIFESTUAC 連結器選項"
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定使用者帳戶控制 \(UAC\) 資訊是否要內嵌在程式資訊清單中。  
  
## 語法  
  
```  
/MANIFESTUAC  
/MANIFESTUAC:NO  
/MANIFESTUAC:fragment  
/MANIFESTUAC:level=_level  
/MANIFESTUAC:uiAccess=_uiAccess  
```  
  
#### 參數  
 `fragment`  
 字串，內含 `level` 和 `uiAccess` 值。  如需詳細資訊，請參閱本主題稍後的「備註」一節。  
  
 `_level`  
 *asInvoker*、*highestAvailable* 或 *requireAdministrator* 其中之一。  預設值為 asInvoker。  如需詳細資訊，請參閱本主題稍後的「備註」一節。  
  
 `_uiAccess`  
 如果您希望應用程式略過使用者介面保護層級，並將輸入放到桌面上更高權限的視窗 \(例如螢幕小鍵盤\)，則為 `true`；否則為 `false`。  預設值為 `false`。  只有針對使用者介面協助工具應用程式時，才設定為 `true`。  
  
## 備註  
 如果您在命令列上指定多個 \/MANIFESTUAC 選項，則最後輸入的選項優先。  
  
 \/MANIFESTUAC:level 的選項如下：  
  
-   `asInvoker`：執行應用程式的使用權限將和啟動應用程式的處理序相同。  選取 \[**以系統管理員身分執行**\] 可以將應用程式提升為較高的使用權限。  
  
-   highestAvailable：應用程式會以所能使用的最高使用權限等級執行。  如果啟動應用程式的使用者是 Administrators 群組的成員，則這個選項就等於 requireAdministrator。  如果最高的可用使用權限等級高於開啟處理序的等級，系統將會提示要求認證。  
  
-   requireAdministrator：應用程式會以系統管理員使用權限執行。  啟動應用程式的使用者必須是 Administrators 群組的成員。  如果開啟處理序不是以系統管理員使用權限執行，系統將會提示要求認證。  
  
 您可以使用 \/MANIFESTUAC:fragment 選項，在一個步驟中指定層級和 uiAccess 值。  該片段必須遵循下列格式：  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**資訊清單檔案**\] 屬性頁。  
  
5.  修改 \[**啟用使用者帳戶控制 \(UAC\)**\]、\[**UAC 執行層級**\] 和 \[**UAC 略過 UI 保護**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)