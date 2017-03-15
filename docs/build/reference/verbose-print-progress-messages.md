---
title: "/VERBOSE (列印進度訊息) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/verbose"
  - "VC.Project.VCLinkerTool.ShowProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/VERBOSE 連結器選項"
  - "相依性 [C++], 連結器輸出中的相依性資訊"
  - "連結器 [C++], 輸出相依性資訊"
  - "連結 [C++], 工作階段進度資訊"
  - "列印進度訊息連結器選項"
  - "VERBOSE 連結器選項"
  - "-VERBOSE 連結器選項"
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /VERBOSE (列印進度訊息)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]  
```  
  
## 備註  
 連結器會將有關連結工作階段進度的資訊傳送到 **\[輸出\]** 視窗。  在命令列上，這項資訊會傳送至標準輸出，也可以重新導向至檔案中。  
  
|選項|說明|  
|--------|--------|  
|\/VERBOSE|顯示有關連結進度的詳細資料。|  
|\/VERBOSE:ICF|顯示關於使用 [\/OPT:ICF](../../build/reference/opt-optimizations.md) 之後所產生連結器活動的資訊。|  
|\/VERBOSE:INCR|顯示有關加入連結程序的資訊。|  
|\/VERBOSE:LIB|只顯示表示所搜尋之程式庫的進度訊息。<br /><br /> 顯示的資訊包括程式庫搜尋進度並列出每一程式庫和目的檔的名稱 \(以完整路徑\)、從程式庫解析的符號，以及參考該符號之目的檔的清單。|  
|\/VERBOSE:REF|顯示關於使用 [\/OPT:REF](../../build/reference/opt-optimizations.md) 之後所產生連結器活動的資訊。|  
|\/VERBOSE:SAFESEH|當未指定 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) 時，顯示哪些模組與安全例外狀況處理不相容的資訊。|  
|\/VERBOSE:UNUSEDLIBS|該影像建立時，顯示有關未使用的所有程式庫檔案的相關資訊。|  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開 \[**連結器**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  加入這個選項在 \[**其他選項**\] 方塊中。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)