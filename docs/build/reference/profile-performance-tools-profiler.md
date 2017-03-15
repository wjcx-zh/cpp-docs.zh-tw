---
title: "/PROFILE (效能工具分析工具) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.Profile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/PROFILE 連結器選項"
  - "-PROFILE 連結器選項"
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /PROFILE (效能工具分析工具)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

產生可以配合效能工具分析工具使用的輸出檔。  
  
## 語法  
  
```  
/PROFILE  
```  
  
## 備註  
 \/PROFILE 隱含下列連結器選項：  
  
-   [\/OPT:REF](../../build/reference/opt-optimizations.md)  
  
-   \/OPT:NOICF  
  
-   [\/INCREMENTAL:NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [\/FIXED:NO](../../build/reference/fixed-fixed-base-address.md)  
  
 \/PROFILE 會使得連結器在程式映像中產生重新配置區段。重新配置區段允許分析工具 \(Profiler\) 轉換程式映像，以取得分析資料。  
  
 **\/PROFILE** 只能在企業 \(小組開發\) 版中使用。如需 PREfast 的詳細資訊，請參閱 [C\/C\+\+ 程式碼分析概觀](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md)。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**進階**\] 屬性頁。  
  
5.  修改 \[**分析**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)