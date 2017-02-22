---
title: "專案建置錯誤 PRJ0003 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0003"
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 專案建置錯誤 PRJ0003
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

繁衍 \(Spawn\) 'command line' 發生錯誤。  
  
 由 \[**屬性頁**\] 對話方塊內的輸入所形成的 ***command line*** 命令傳回了一個錯誤碼，但 \[輸出\] 視窗中未出現任何資訊。  
  
 這個錯誤的可能原因是：  
  
-   您的專案相依於 ATL Server。  從 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 開始，ATL Server 不再是 Visual Studio 的一部分，而是在 CodePlex 當做共用原始程式碼的專案來發行。  若要下載 ATL Server 原始程式碼和工具，請前往[http:\/\/go.microsoft.com\/fwlink\/?LinkID\=81979](http://go.microsoft.com/fwlink/?LinkID=81979)。  
  
-   系統資源過低。  請關閉部分應用程式來解決這個問題。  
  
-   安全性特殊權限不足。  請驗證您是否具有充分的安全性特殊權限。  
  
-   [VC\+\+ 目錄](http://msdn.microsoft.com/zh-tw/e027448b-c811-4c3d-8531-4325ad3f6e02)中指定的可執行檔路徑，不包括您嘗試執行之工具的路徑。  
  
-   就 makefile 專案而言，您遺漏在 \[建置命令列\] 或 \[重建命令列\] 上執行的命令。  
  
## 請參閱  
 [專案組建錯誤和警告 \(PRJxxxx\)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)