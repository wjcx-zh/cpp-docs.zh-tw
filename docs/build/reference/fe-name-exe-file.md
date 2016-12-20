---
title: "/Fe (命名 EXE 檔案) | Microsoft Docs"
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
  - "/fe"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fe 編譯器選項 [C++]"
  - "可執行檔, 重新命名"
  - "Fe 編譯器選項 [C++]"
  - "-Fe 編譯器選項 [C++]"
  - "重新命名檔案編譯器選項 [C++]"
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Fe (命名 EXE 檔案)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定由編譯器所建立 .exe 檔案或 DLL 的名稱和目錄。  
  
## 語法  
  
```  
/Fepathname  
```  
  
## 備註  
 不使用這個選項的話，編譯器會使用第一個原始程式檔或命令列上指定的目的檔的主檔名，再加上副檔名 .exe 或 .dll 來賦予該檔案預設的名稱。  
  
 如果您指定 [\/c \(編譯而不連結\)](../../build/reference/c-compile-without-linking.md)，在沒有連結下進行編譯，**\/Fe** 將不會有作用。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**一般**\] 屬性頁。  
  
4.  修改 \[**輸出檔**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## 範例  
 以下命令列會編譯及連結目前目錄中的所有 C 原始程式檔。  產生的可執行檔被命名為 PROCESS.exe 並且會建立在 C:\\BIN 目錄中。  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## 範例  
 以下命令列會在 `C:\BIN` 中建立一個主檔名與第一個原始程式檔或目的檔相同的可執行檔：  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)