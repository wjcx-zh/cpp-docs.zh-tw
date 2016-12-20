---
title: "/ERRORREPORT (回報內部連結器錯誤) | Microsoft Docs"
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
  - "/ERRORREPORT"
  - "VC.Project.VCLinkerTool.ErrorReporting"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ERRORREPORT 連結器選項"
  - "ERRORREPORT 連結器選項"
  - "-ERRORREPORT 連結器選項"
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ERRORREPORT (回報內部連結器錯誤)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## 備註  
 讓您直接向 Microsoft 提供內部編譯器錯誤 \(ICE\) 資訊。  
  
 選項 **\/errorReport:send** 會嘗試自動將錯誤資訊傳送至 Microsoft，但成功與否取決於登錄設定。  如需在登錄中設定適當值的詳細資訊，請參閱 MSDN 網站上的[如何在 Visual Studio 2008 命令列工具中開啟自動錯誤報告](http://go.microsoft.com/fwlink/?LinkID=184695)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**組態屬性**\] 資料夾。  
  
3.  按一下 \[**連結器**\] 資料夾。  
  
4.  按一下 \[**進階**\] 屬性頁。  
  
5.  修改 \[**錯誤報告**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>。  
  
## 請參閱  
 [\/errorReport \(回報編譯器內部錯誤\)](../../build/reference/errorreport-report-internal-compiler-errors.md)   
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)