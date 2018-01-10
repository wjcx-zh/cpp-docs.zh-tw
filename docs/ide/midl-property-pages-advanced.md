---
title: "MIDL 屬性頁： 進階 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
dev_langs: C++
helpviewer_keywords: MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6e7dde047c3311c6fd694a91c7a63fcfbcc95d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="midl-property-pages-advanced"></a>MIDL 屬性頁：進階
**進階**中的 屬性頁**MIDL**資料夾指定下列的 MIDL 編譯器選項：  
  
-   啟用錯誤檢查 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   檢查配置 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   檢查界限 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   檢查列舉範圍 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   請檢查參考指標 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   檢查 Stub 資料 ([/error](http://msdn.microsoft.com/library/windows/desktop/aa367324))  
  
-   驗證參數 ([/ 強固](http://msdn.microsoft.com/library/windows/desktop/aa367363)) *  
  
-   結構成員對齊 ([/Zp](http://msdn.microsoft.com/library/windows/desktop/aa367388))  
  
-   將輸出重新導向 ([/o](http://msdn.microsoft.com/library/windows/desktop/aa367351))  
  
-   C 前置處理選項 ([/cpp_opt](http://msdn.microsoft.com/library/windows/desktop/aa367318))  
  
-   取消前置處理器定義 ([/U](http://msdn.microsoft.com/library/windows/desktop/aa367373))  
  
 \*/ 穩定時，只用於建置適用於 Windows 2000 或更新版本的電腦。 如果您建置 ATL 專案，而且想要使用 / 強固、 變更 dlldatax.c 檔中的這一行：  
  
```  
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM  
to   
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM  
```  
  
 如需有關如何存取詳細**進階**中的 屬性頁**MIDL**資料夾，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
 如需如何以程式設計方式存取 c + + 專案的 MIDL 選項的資訊，請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>。  
  
## <a name="see-also"></a>請參閱  
 [MIDL 屬性頁](../ide/midl-property-pages.md)