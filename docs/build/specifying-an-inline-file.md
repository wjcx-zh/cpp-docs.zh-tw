---
title: "指定內嵌檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案 [C++], 內嵌"
  - "內嵌檔 [C++], 指定 NMAKE"
  - "NMAKE 程式, 內嵌檔"
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 指定內嵌檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在出現 *filename*  的命令中指定兩個角括弧 \(\<\<\)。  角括弧不能是巨集展開。  
  
## 語法  
  
```  
<<[filename]  
```  
  
## 備註  
 執行命令時，*filename* \(如果有指定\) 或由 NMAKE 所產生的唯一名稱就會取代角括弧。  如果有指定，*filename* 必須要跟隨在角括弧之後，不可以有空白或定位字元。  允許使用路徑。  不需要或假設副檔名。  如果有指定 *filename*，就會在目前的或指定的目錄中建立檔案，並覆寫具有該名稱的任何現有檔案，否則便會建立在 TMP 目錄 \(或者如果未定義 TMP 環境變數，則建立在目前的目錄內\)。  如果重複使用先前的 *filename*，NMAKE 會取代之前的檔案。  
  
## 請參閱  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)