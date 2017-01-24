---
title: "C++ 標準程式庫概觀 | Microsoft Docs"
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
  - "頁首, C++ 程式庫"
  - "程式庫, Standard C++"
  - "Standard C++ 程式庫"
  - "Standard C++ 程式庫, 頁首"
ms.assetid: 7acb83a4-da73-4ad3-bc30-a71289db7f60
caps.latest.revision: 16
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 標準程式庫概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所有 C\+\+ 程式庫實體都會在一或多個標準標頭中宣告或定義。  此實作包含 C\+\+ Standard 不需要的額外兩個標頭 \(`<hash_map>` 和 `<hash_set>`\)。  如需此實作支援的完整標頭清單，請參閱[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)。  
  
 C\+\+ 程式庫的獨立式實作僅提供這些標頭的子集：  
  
|||  
|-|-|  
|[\<cstddef\>](../standard-library/cstddef.md)|[\<cstdlib\>](../standard-library/cstdlib.md) \(至少宣告 `abort`、`atexit` 和 `exit` 函式\)|  
|[\<exception\>](../standard-library/exception.md)|[\<limits\>](../standard-library/limits.md)|  
|[\<new\>](../standard-library/new.md)|[\<cstdarg\>](../standard-library/cstdarg.md)|  
  
 C\+\+ 程式庫標頭有兩個更廣泛的細分：  
  
-   [iostreams](../standard-library/iostreams-conventions.md) 慣例。  
  
-   [標準樣板程式庫](../misc/standard-template-library.md)慣例。  
  
 本節包含下列小節：  
  
-   [使用 C\+\+ 程式庫標頭](../standard-library/using-cpp-library-headers.md)  
  
-   [C\+\+ 程式庫慣例](../standard-library/cpp-library-conventions.md)  
  
-   [iostreams 慣例](../standard-library/iostreams-conventions.md)  
  
-   [C\+\+ 程式啟動和終止](../standard-library/cpp-program-startup-and-termination.md)  
  
-   [安全程式庫：C\+\+ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)  
  
-   [已檢查的迭代器](../standard-library/checked-iterators.md)  
  
-   [偵錯迭代器支援](../standard-library/debug-iterator-support.md)  
  
-   [標準樣板程式庫](../misc/standard-template-library.md)  
  
-   [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)  
  
-   [stdext 命名空間](../standard-library/stdext-namespace.md)  
  
-   [規則運算式 \(C\+\+\)](../standard-library/regular-expressions-cpp.md)  
  
 如需 Visual C\+\+ 執行階段程式庫的詳細資訊，請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  
  
## 請參閱  
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)