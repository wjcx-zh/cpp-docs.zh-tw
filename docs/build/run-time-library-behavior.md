---
title: "執行階段程式庫行為 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_DllMainCRTStartup"
  - "CRT_INIT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_INIT 巨集"
  - "_DllMainCRTStartup 方法"
  - "DllMain 函式"
  - "DLL [C++], 進入點函式"
  - "DLL [C++], 執行階段程式庫行為"
  - "DLL [C++], 啟動順序"
  - "處理序附加 [C++]"
  - "處理序中斷連結 [C++]"
  - "執行階段 [C++], DLL 啟動順序"
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 執行階段程式庫行為
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\/C\+\+ 執行階段程式庫程式碼執行 DLL 啟動順序，減少像在 Windows 3.x 必須連結不同模組的步驟。  包含在 C\/C\+\+ Run\-Time 程式庫程式碼的是名為 **\_DllMainCRTStartup** 的 DLL 進入點函式。  這個 **\_DllMainCRTStartup** 函式可以完成許多事，包括呼叫 **\_CRT\_INIT**，其可初始化 C\/C\+\+ 執行階段程式庫，並且在靜態、非區域變數上叫用 \(Invoke\) C\+\+ 建構函式。  如果沒有這個函式，執行階段程式庫就會停留在未初始化的狀態。  **\_CRT\_INIT** 可用於從使用者 DLL 靜態連結的 CRT，或動態連結的 CRT DLL Msvcr90.dll。  
  
 雖然可以使用 \/ENTRY: 連結器選項來指定另一個進入點函式，我們不建議您這麼做，因為您的進入點函式將會需要重複 **\_DllMainCRTStartup** 所做的每件事。  **\_DllMainCRTStartup** 會在 Visual C\+\+ 裡建置 DLL 時自動連結，而且您也不需要使用 \/ENTRY: 連結器選項來指定進入點函式。  
  
 **\_DllMainCRTStartup** 除了可以用來初始化 C 執行階段程式庫，還可呼叫名為 `DllMain` 的函式。  Visual C\+\+ 會根據您要建置的 DLL 類型來提供 `DllMain` 並加以連結，所以 **\_DllMainCRTStartup** 一定有東西可以呼叫。  這樣一來，如果您不需要初始化 DLL，則在建置 DLL 時就沒有特別的注意事項了。  如果您需要初始化您的 DLL，您就必須根據 DLL 的撰寫類型來判斷在何處加入您的程式碼。  如需詳細資訊，請參閱[初始化 DLL](../build/initializing-a-dll.md)。  
  
 C\/C\+\+ 執行階段程式庫程式碼會在靜態、非區域變數上呼叫建構函式和解構函式 \(Destructor\)。  例如，在下列 DLL 原始程式碼中，`Equus` 和 `Sugar` 定義於 Horses.h，為兩個 `CHorse` 類別之靜態、非區域物件。  因為這些物件是定義在任何函式之外，所以原始程式碼中不會包含呼叫 `CHorse` 建構函式或解構函式的函式。  因此，這些建構函式和解構函式的呼叫必須由執行階段程式碼執行。  應用程式的執行階段程式庫程式碼也會執行這個函式。  
  
```  
#include "horses.h"  
  
CHorse  Equus( ARABIAN, MALE );  
CHorse  Sugar( THOROUGHBRED, FEMALE );  
  
BOOL    WINAPI   DllMain (HANDLE hInst,   
                            ULONG ul_reason_for_call,  
                            LPVOID lpReserved)  
...  
```  
  
 每一次新處理序嘗試使用 DLL 時，作業系統會建立不同的 DLL 資料複本：這稱為處理序附加。  DLL 的執行階段程式庫程式碼會呼叫所有全域物件的建構函式 \(如果有的話\)，接著再以選取的處理序連結呼叫 `DllMain` 函式。  相反的情況是處理序中斷連結：即執行階段程式庫程式碼會以選取的處理序中斷連結來呼叫 `DllMain`，然後呼叫終止函式清單，包括 `atexit` 函式、全域物件的解構函式和靜態物件的解構函式。  請注意，處理序連結中事件的順序是處理序中斷連結的相反方向。  
  
 在執行緒連結和執行緒中斷連結期間也會呼叫執行階段程式庫程式碼，然而執行階段程式碼不會自行初始化或終止。  
  
## 您想要執行甚麼工作？  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)