---
title: "執行緒控制的 C 執行階段程式庫函式 | Microsoft Docs"
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
  - "_beginthread 函式"
  - "_beginthreadex 函式"
  - "_endthread 函式"
  - "_endthreadex 函式"
  - "多執行緒 [C++], 控制執行緒"
  - "執行緒 [C++], 控制執行緒"
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 執行緒控制的 C 執行階段程式庫函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所有的 Win32 程式都至少擁有一個執行緒。  任何執行緒都可以建立其他的執行緒。  執行緒可以快速完成工作然後終止，或者它可以在程式的存留期裡保持為作用中。  
  
 LIBCMT 和 MSVCRT 為 C 的執行階段程式庫，會針對執行緒的建立和終止提供下列函式：[\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 和 [\_endthread、\_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。  
  
 如果作業成功，`_beginthread` 和 `_beginthreadex` 函式會建立新的執行緒，並傳回執行緒識別項。  如果執行緒完成執行，就會自動結束，或者也可以呼叫 `_endthread` 或 `_endthreadex` 來結束。  
  
> [!NOTE]
>  如果您要從以 Libcmt.lib 建置的程式來呼叫 C 執行階段常式，您必須使用 `_beginthread` 或 `_beginthreadex` 函式來啟動執行緒。  請不要使用 Win32 函式 `ExitThread` 和 `CreateThread`。  當一個以上的執行緒遭到阻擋，且等候暫停執行緒完成它對 C 的執行階段資料結構的存取時，使用 `SuspendThread` 可能會造成死結 \(Deadlock\)。  
  
##  <a name="_core_the__beginthread_function"></a> \_beginthread 和 \_beginthreadex 函式  
 `_beginthread` 和 `_beginthreadex` 函式會建立新的執行緒。  和處理序中其他執行緒共用處理序的程式碼和資料區段 \(Data Segment\) 之執行緒，但是擁有自己唯一的登錄值、堆疊空間和目前的指令位址。  系統將 CPU 時間分給每個執行緒，因此處理序裡的所有執行緒可以並行執行。  
  
 `_beginthread` 和 `_beginthreadex` 類似於 Win32 API 中的 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函式，但是有下列差異：  
  
-   它們會初始化某些 C 執行階段程式庫變數。  只有當您在執行緒裡使用 C 的執行階段程式庫時，這項功能才具有重要性。  
  
-   `CreateThread` 提供對安全屬性的控制項。  您可以使用這個函式來啟動在暫停狀態中的執行緒。  
  
 如果作業成功，`_beginthread` 和 `_beginthreadex` 會將控制代碼傳給新的執行緒；如果有錯誤發生，則是傳回錯誤碼。  
  
##  <a name="_core_the__endthread_function"></a> \_endthread 和 \_endthreadex 函式  
 [\_endthread](../c-runtime-library/reference/endthread-endthreadex.md) 函式會結束由 `_beginthread` 所建立的執行緒 \(同樣地，`_endthreadex` 會結束由 `_beginthreadex` 所建立的執行緒\)。  當執行緒完成時，會自動結束。  `_endthread` 和 `_endthreadex` 對於從執行緒進行條件式終止非常實用。  例如，專門用於通訊處理的執行緒可能會結束，除非它取得通訊連接埠的控制。  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)