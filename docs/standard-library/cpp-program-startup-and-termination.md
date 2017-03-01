---
title: "C++ 程式啟動和終止 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 53e31f3f3a175013a248401f4231bb87cf444681
ms.lasthandoff: 02/24/2017

---
# <a name="c-program-startup-and-termination"></a>C++ 程式啟動和終止
C++ 程式執行的作業和 C 程式在執行程式啟動和程式終止時執行的相同，再加上幾個此處概述的作業。  
  
 在目標環境呼叫 `main` 函式之前，以及其儲存任何常數初始值 (您在具有靜態期間的所有物件中所指定) 之後，程式即會針對這類靜態物件執行任何剩餘的建構函式。 系統不會指定轉譯單位之間的執行順序，但您仍可假設這些靜態建構函式已正確初始化所要使用的部分 [iostreams](../standard-library/iostreams-conventions.md) 物件。 這些控制文字資料流如下：  
  
-   [cin](../standard-library/iostream.md#cin) — 適用於標準輸入。  
  
-   [cout](../standard-library/iostream.md#cout) — 適用於標準輸出。  
  
-   [cerr](../standard-library/iostream.md#cerr) — 適用於非緩衝的標準錯誤輸出。  
  
-   [clog](../standard-library/iostream.md#clog) — 適用於緩衝的標準錯誤輸出。  
  
 於程式終止期間，您也可以在針對靜態物件呼叫的解構函式內使用這些物件。  
  
 和使用 C 相同，從 `main` 傳回或進行`exit` 呼叫時，系統會依據登錄的相反順序，呼叫在 `atexit` 中登錄的所有函式。 從這類已登錄函式擲回的例外狀況皆會呼叫 `terminate`。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



