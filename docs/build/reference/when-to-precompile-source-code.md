---
title: "先行編譯原始程式碼的時機 | Microsoft Docs"
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
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "先行編譯標頭檔, 先行編譯的時機"
  - "原始程式碼, 先行編譯"
ms.assetid: eb8ba193-fd87-40d3-9545-c75deabe37cb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 先行編譯原始程式碼的時機
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

開發程式時，先行編譯程式碼可以有效減少編輯時間，特別是在下列情況時：  
  
-   使用不常變更的大型程式碼主體。  
  
-   程式中包括多個模組，這些模組全部使用一組標準的 include 檔和相同的編譯選項。  在此情況下，全部的 include 檔可先行編譯成一個先行編譯標頭。  
  
 第一次編譯會建立先行編譯標頭檔 \(Precompiled Header File\)，會比後續的編譯需要稍長的時間。  後續的編譯由於包含先行編譯程式碼而可更快地編譯。  
  
 您可以先行編譯 C 和 C\+\+ 這兩種程式。  在 C\+\+ 程式設計中，一般會將類別介面資訊分開至標頭檔。  稍後可將這些標頭檔加入到使用該類別的程式。  先行編譯這些標頭後，即可減少程式編譯所需的時間。  
  
> [!NOTE]
>  雖然每個原始程式檔只能有一個先行編譯標頭檔 \(.pch\)，不過您可在一個專案內使用多個 .pch 檔。  
  
## 請參閱  
 [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)