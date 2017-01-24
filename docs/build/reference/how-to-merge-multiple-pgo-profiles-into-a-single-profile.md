---
title: "如何：將多個 PGO 設定檔合併至單一設定檔 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "合併設定檔"
  - "特性指引最佳化, 合併設定檔"
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：將多個 PGO 設定檔合併至單一設定檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

特性指引最佳化 \(PGO\) 是一個很好用的工具，它可以依據已剖析的案例來建立最佳化的二進位檔。  但如果應用程式具有幾個重要而又不同的案例，您要如何建立單一設定檔，讓 PGO 可以在數個不同的案例中使用呢？  在 Visual Studio 中，PGO 管理員 Pgomgr.exe 會替您解決這個問題。  
  
 合併設定檔的語法如下：  
  
```  
pgomgr /merge[:num] [.pgc_files] .pgd_files  
```  
  
 其中 `num` 是一個用於這項合併作業的選擇性權數。  如果有某些案例比其他案例重要，或者如果有必須執行多次的案例，通常會使用權數。  
  
> [!NOTE]
>  PGO 管理員不會處理過時的設定檔資料。  若要將 .pgc 檔合併成 .pgd 檔，則產生 .pgc 檔的可執行檔必須是由產生 .pgd 檔的相同引動過程所建立。  
  
## 範例  
 在本範例中，PGO 管理員會將 pgcFile.pgc 加入至 pgdFile.pgd 六次。  
  
```  
pgomgr /merge:6 pgcFile.pgc pgdFile.pgd  
```  
  
## 範例  
 在本範例中，PGO 管理員會將 pgcFile1.pgc 和 pgcFile2.pgc 加入至 pgdFile.pgd，每一個 .pgc 檔都加入兩次。  
  
```  
pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd  
```  
  
## 範例  
 如果 PGO 管理員是在沒有指定 .pgc 檔的情況下執行，它會搜尋本機目錄，以便找出和 .pgd 檔具有相同名稱並且附加了驚嘆號 \(\!\) 後面又跟著任意字元的所有 .pgc 檔。  如果本機目錄中有 test.pgd、test\!1.pgc、test2.pgc 以及 test\!hello.pgc 等檔案，並且下列命令是從該本機目錄中執行，那麼 test\!1.pgc 和 test\!hello.pgc 就會被合併到 test.pgd 中。  
  
```  
pgomgr /merge test.pgd  
```  
  
## 請參閱  
 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)