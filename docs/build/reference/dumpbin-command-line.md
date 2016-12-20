---
title: "DUMPBIN 命令列 | Microsoft Docs"
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
  - "dumpbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DUMPBIN 程式, 命令列"
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# DUMPBIN 命令列
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要執行 DUMPBIN，請使用下列語法：  
  
```  
DUMPBIN [options] files...  
```  
  
 指定一個或多個二進位檔案，連同控制資訊所需的任何選項。  DUMPBIN 會將資訊顯示於標準輸出。  您可將它重新導向到檔案或使用 \/OUT 選項來指定輸出的檔名。  
  
 當您針對檔案執行 DUMPBIN 時，如果沒有指定任何選項，DUMPBIN 會顯示 \/SUMMARY 輸出。  
  
 當您輸入 `dumpbin` 命令，而沒有包括其他任何命令列輸入時，DUMPBIN 會顯示一份摘要其選項的用法說明。  
  
## 請參閱  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)   
 [DUMPBIN 參考](../../build/reference/dumpbin-reference.md)