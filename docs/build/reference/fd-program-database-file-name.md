---
title: "/Fd (程式資料庫檔名) | Microsoft Docs"
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
  - "/FD"
  - "VC.Project.VCCLWCECompilerTool.ProgramDataBaseFileName"
  - "VC.Project.VCCLCompilerTool.ProgramDataBaseFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 建立"
  - "/FD 編譯器選項 [C++]"
  - "FD 編譯器選項 [C++]"
  - "-FD 編譯器選項 [C++]"
  - "PDB 檔案, 建立"
  - "program database 編譯器選項 [C++]"
  - "程式資料庫檔案名稱 [C++]"
ms.assetid: 3977a9ed-f0ac-45df-bf06-01cedd2ba85a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fd (程式資料庫檔名)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定由 [\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md) 所建立之程式資料庫 \(PDB\) 檔案的檔名。  
  
## 語法  
  
```  
/Fdpathname  
```  
  
## 備註  
 若不使用 **\/Fd**，PDB 檔名會預設值為 VC`x`0.pdb，其中 `x` 為所使用 Visual C\+\+ 的主要版本。  
  
 如果您指定不包括檔名的路徑名稱 \(該路徑是以反斜線結尾\)，則編譯器會在指定的目錄中建立名為 VC`x`0.pdb. 的 .pdb 檔  
  
 如果您指定一個不包括副檔名的檔名，編譯器會使用 .pdb 做為副檔名。  
  
 這個選項也會命名使用於最少重建和累加編譯的狀態 \(.idb\) 檔案。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**輸出檔**\] 屬性頁。  
  
4.  修改 \[**程式資料庫檔名**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ProgramDataBaseFileName%2A>。  
  
## 範例  
 這個命令列會建立一個名為 PROG.pdb 的 .pdb 檔案和一個名為 PROG.idb 的 .idb 檔案：  
  
```  
CL /DDEBUG /Zi /FdPROG.PDB PROG.CPP  
```  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)