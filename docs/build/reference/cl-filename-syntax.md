---
title: "CL 檔名語法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "cl.exe 編譯器, 檔名語法"
  - "擴充功能, 指定至編譯器"
  - "檔案名稱 [C++]"
  - "檔案名稱 [C++], CL 編譯器"
  - "路徑, CL 編譯器檔名語法"
  - "語法, 編譯器檔名"
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# CL 檔名語法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CL 可以接受其名稱遵循 FAT、HPFS 或 NTFS 命名慣例的檔案。  任何檔名都可以包含完整或部分路徑。  完整路徑包括磁碟機名稱和一個或多個目錄名稱。  CL 可以接受以反斜線 \(\\\) 或正斜線 \(\/\) 分隔的檔名。  包含空格的檔名必須以雙引號字元括起來。  部分路徑省略磁碟機名稱，CL 會假設為目前的磁碟機。  如果您不指定路徑，CL 會假設檔案是在目前的目錄。  
  
 副檔名決定檔案的處理方式。  會編譯副檔名為.c、.cxx 或 .cpp 的 C 和 C\+\+ 檔案。  其他檔案，包括 .obj 檔案、程式庫 \(.lib\) 和模組定義 \(.def\) 檔，會不經處理即直接傳遞至連結器。  
  
## 請參閱  
 [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)