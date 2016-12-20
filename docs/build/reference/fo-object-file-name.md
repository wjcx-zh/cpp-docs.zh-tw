---
title: "/Fo (目的檔名稱) | Microsoft Docs"
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
  - "/Fo"
  - "VC.Project.VCCLCompilerTool.ObjectFile"
  - "VC.Project.VCCLWCECompilerTool.ObjectFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fo 編譯器選項 [C++]"
  - "Fo 編譯器選項 [C++]"
  - "-Fo 編譯器選項 [C++]"
  - "目的檔, 命名"
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fo (目的檔名稱)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定要用來取代預設值的目的檔 \(.obj\) 名稱或目錄。  
  
## 語法  
  
```  
/Fopathname  
```  
  
## 備註  
 如果您不使用這個選項，目的檔會使用原始程式檔的主檔名和 .obj 副檔名。  您可以使用您想要的任何名稱和副檔名，不過建議的慣例是使用 .obj。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**輸出檔**\] 屬性頁。  
  
4.  修改 \[**目的檔名稱**\] 屬性。在開發環境中，目的檔必須有副檔名 .obj。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>。  
  
## 範例  
 以下命令列會在 B 磁碟上的現有目錄 \(\\OBJECT\) 中建立一個名為 THIS.obj 的目的檔。  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)