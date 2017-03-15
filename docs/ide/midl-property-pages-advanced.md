---
title: "MIDL 屬性頁：進階 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCMidlTool.ErrorCheckBounds"
  - "VC.Project.VCMidlTool.ErrorCheckStubData"
  - "VC.Project.VCMidlTool.ErrorCheckAllocations"
  - "VC.Project.VCMidlTool.CPreprocessOptions"
  - "VC.Project.VCMidlTool.UndefinePreprocessorDefinitions"
  - "VC.Project.VCMidlTool.EnableErrorChecks"
  - "VC.Project.VCMidlTool.RedirectOutputAndErrors"
  - "VC.Project.VCMidlTool.ErrorCheckEnumRange"
  - "VC.Project.VCMidlTool.StructMemberAlignment"
  - "VC.Project.VCMidlTool.ErrorCheckRefPointers"
  - "VC.Project.VCMidlTool.ValidateParameters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MIDL, 屬性頁"
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MIDL 屬性頁：進階
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\[MIDL\] 資料夾的 \[進階\] 屬性頁會指定下列的 MIDL 編譯器選項：  
  
-   啟用錯誤檢查 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   檢查配置 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   檢查限制 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   檢查列舉類型範圍 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   檢查參考指標 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   檢查 Stub 資料 \([\/error](http://msdn.microsoft.com/library/windows/desktop/aa367324)\)  
  
-   驗證參數 \([\/robust](http://msdn.microsoft.com/library/windows/desktop/aa367363)\)  
  
-   結構成員對齊 \([\/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388)\)  
  
-   重新導向輸出 \([\/o](http://msdn.microsoft.com/library/windows/desktop/aa367351)\)  
  
-   C 前置處理器選項 \([\/cpp\_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318)\)  
  
-   取消前置處理器的定義 \([\/U](http://msdn.microsoft.com/library/windows/desktop/aa367373)\)  
  
 \* \/robust 只適用於建置 Windows 2000 或以上版本的電腦。  如果您建置 ATL 專案時想要使用 \/robust，請變更 dlldatax.c 檔中的這一行：  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 如需如何存取 \[MIDL\] 資料夾中 \[進階\] 屬性頁的詳細資訊，請參閱 [HOW TO：使用屬性頁指定專案屬性](../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
 如需如何利用程式存取 C\+\+ 專案之 MIDL 選項的資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>。  
  
## 請參閱  
 [MIDL 屬性頁](../ide/midl-property-pages.md)