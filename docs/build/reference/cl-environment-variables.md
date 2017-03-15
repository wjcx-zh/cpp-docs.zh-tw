---
title: "CL 環境變數 | Microsoft Docs"
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
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器, 環境變數"
  - "環境變數, CL 編譯器"
  - "INCLUDE 環境變數"
  - "LIBPATH 環境變數"
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CL 環境變數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL 工具使用下列環境變數：  
  
-   CL 和 \_CL\_ \(若已定義\)。  在處理之前，CL 工具會在前面加上 CL 環境變數中定義的引數選項和引數，並在後面附加 \_CL\_ 中定義的選項和引數。  
  
-   INCLUDE，必須指向 Visual C\+\+ 安裝的 \\include 子目錄。  
  
-   LIBPATH，指定要針對以 [\#using](../../preprocessor/hash-using-directive-cpp.md) 參考之中繼資料檔案搜尋的目錄。  如需 LIBPATH 的詳細資訊，請參閱 `#using`。  
  
 您可以設定使用下列語法設定 CL 或 \_CL\_ 環境變數：  
  
```  
SET CL=[ [option] ... [file] ...] [/link link-opt ...]  
SET _CL_=[ [option] ... [file] ...] [/link link-opt ...]  
```  
  
 如需 CL 和 \_CL\_ 環境變數之引數的詳細資訊，請參閱[編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)。  
  
 您可以使用這些環境變數來定義您最常使用的檔案與選項，並使用命令列來定義用於特定用途的特定檔案和選項。  CL 和 \_CL\_ 環境變數限制為 1024 個字元 \(命令列輸入限制\)。  
  
 您無法使用 \/D 選項來定義使用等號 \(\=\) 的符號。  您可以將等號取代為數字符號 \(\#\)。  如此一來，您可以使用 CL 或 \_CL\_ 環境變數，以明確值定義前置處理器常數 — 例如，`/DDEBUG#1` 以定義 `DEBUG=1`。  
  
 如需相關資訊，請參閱[設定環境變數](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
## 範例  
 以下是設定 CL 環境變數的範例：  
  
```  
SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ  
```  
  
 當設定這個環境變數時，如果您在命令列中輸入 `CL INPUT.C`，這是有效的命令：  
  
```  
CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C  
```  
  
 下列範例會造成一般 CL 命令編譯原始程式檔 FILE1.c 和 FILE2.c，然後再連結物件檔案 FILE1.obj、FILE2.obj 和 FILE3.obj：  
  
```  
SET CL=FILE1.C FILE2.C  
SET _CL_=FILE3.OBJ  
CL  
  
```  
  
 這個範例具有與下列命令列相同的效果：  
  
```  
CL FILE1.C FILE2.C FILE3.OBJ  
```  
  
## 請參閱  
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)