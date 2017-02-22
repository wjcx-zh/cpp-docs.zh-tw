---
title: "命令列的資訊清單產生過程 | Microsoft Docs"
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
  - "資訊清單工具 (mt.exe)"
  - "資訊清單 [C++]"
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 命令列的資訊清單產生過程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用 nmake 或類似的工具從命令列建置 C\/C\+\+ 應用程式時，會在連結器已處理完所有物件檔案及建置最終程式庫之後，產生資訊清單。  連結器會收集儲存在目的檔中的組件資訊，然後將此資訊組合成最終資訊清單檔。  根據預設，連結器會產生一個稱為 \<binary\_name\>.\<extension\>.manifest 的檔案，以描述最終二進位檔。  連結器不會將資訊清單檔內嵌於二進位檔中，它只能產生做為外部檔案的資訊清單。  有幾個方式可以將資訊清單內嵌於最終二進位檔中，例如使用[資訊清單工具 \(mt.exe\)](http://msdn.microsoft.com/library/aa375649)，或是將資訊清單編譯成資源檔。  將資訊清單內嵌於最終二進位檔中時，必須遵循特定規則，以便啟用像是累加連結、簽章以及編輯後繼續等功能，這一點很重要，您務必要牢記。  在命令列上建置時，這些選項和其他選項會在 [如何：在 C\/C\+\+ 應用程式中嵌入資訊清單](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)中討論。  
  
## 請參閱  
 [資訊清單](http://msdn.microsoft.com/library/aa375365)   
 [\/INCREMENTAL \(以累加方式連結\)](../build/reference/incremental-link-incrementally.md)   
 [強式名稱組件 \(組件簽署\)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [編輯後繼續](../Topic/Edit%20and%20Continue.md)   
 [了解 C\/C\+\+ 程式的資訊清單產生過程](../build/understanding-manifest-generation-for-c-cpp-programs.md)