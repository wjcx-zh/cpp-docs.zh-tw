---
title: "發行的組建 | Microsoft Docs"
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
  - "偵錯組建, 轉換至發行組建"
  - "偵錯 [C++], 發行組建"
  - "發行組建"
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 發行的組建
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

發行的組建 \(Release Build\) 會採取最佳化；  當您使用最佳化建立發行組建時，編譯器不會產生符號偵錯資訊 \(Symbolic Debugging Information\)。  當沒有符號偵錯資訊，且 TRACE 和 ASSERT 呼叫並未產生程式碼時，表示您的可執行檔已縮小，執行速度將因此而加快。  
  
 本章節提供的資訊說明從偵錯版變更為發行組建的原因和時機。  同時也說明從偵錯版變更為發行組建時可能會遇到的部分問題：  
  
-   [建立發行的組建](../../build/reference/how-to-create-a-release-build.md)  
  
-   [建立發行組建時的常見問題](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)  
  
    -   [檢查 ASSERT 陳述式](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [使用偵錯版檢查記憶體覆寫](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [偵錯發行的組建](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [檢查記憶體覆寫](../../build/reference/checking-for-memory-overwrites.md)  
  
## 請參閱  
 [在 Visual Studio 中建置 C\+\+ 專案](../../ide/building-cpp-projects-in-visual-studio.md)   
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)