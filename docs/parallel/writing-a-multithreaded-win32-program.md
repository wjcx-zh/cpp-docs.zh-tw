---
title: 撰寫多執行緒的 Win32 程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98abce752ca02e40be68787d06fa8d4c17ce3e4b
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131199"
---
# <a name="writing-a-multithreaded-win32-program"></a>撰寫多執行緒 Win32 程式
當您撰寫多個執行緒的程式時，您必須協調其行為與[程式的資源使用](#_core_sharing_common_resources_between_threads)。 您也必須確定每個執行緒會收到[自己的堆疊](#_core_thread_stacks)。  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> 一般執行緒之間共用資源  
  
> [!NOTE]
>  從 MFC 的觀點來看類似的討論，請參閱[多執行緒： 程式設計提示](multithreading-programming-tips.md)並[多執行緒： 何時使用同步類別](multithreading-when-to-use-the-synchronization-classes.md)。  
  
每個執行緒都有它自己的堆疊，以及它自己的複本的 CPU 暫存器。 其他資源，例如檔案、 靜態資料和堆積記憶體中所共用的所有執行緒程序。 使用這些常見資源的執行緒必須進行同步處理。 Win32 提供數種方式來同步處理資源，包括信號、 關鍵區段、 事件和 mutex。  
  
當多個執行緒同時存取靜態資料時，您的程式必須提供可能的資源衝突。 請考慮一個執行緒更新靜態資料結構，包含計劃*x*，*y*要由另一個執行緒顯示項目的座標。 如果更新執行緒改變*x*被優先佔用，才能將變更和座標*y*座標，顯示執行緒可能會排程之前*y*座標是更新。 此項目會顯示在錯誤的位置。 您可以使用信號控制結構的存取來避免這個問題。  
  
Mutex (簡稱*里西斯 mut*ual *ex*clusion) 是一種執行緒或以非同步方式執行的另一個處理序之間進行通訊。 此通訊是通常用來控制共用資源的存取權的鎖定和解除鎖定的資源通常協調多個執行緒或處理程序的活動。 若要解決這個問題*x*，*y*座標更新問題，請更新執行緒會設定指出資料結構正在執行更新之前的使用中的 mutex。 這兩個座標必須處理完之後，它會清除 mutex。 顯示執行緒必須等待要更新顯示之前先釐清 mutex。 這個程序的等候 mutex 通常稱為封鎖 mutex，因為程序遭到封鎖，直到 mutex 清除，才能繼續。  
  
Bounce.c 程式中所示[多執行緒 C 程式範例](sample-multithread-c-program.md)使用具名 mutex`ScreenMutex`協調畫面更新。 它會呼叫其中一個顯示執行緒已準備好撰寫至畫面中，每次`WaitForSingleObject`使用的控制代碼`ScreenMutex`和常數，表示無限`WaitForSingleObject`呼叫應該封鎖 mutex 和逾時。如果`ScreenMutex`很清楚，讓其他執行緒不會干擾顯示設定 mutex wait 函式，並繼續執行執行緒。 否則，執行緒封鎖，直到 mutex 清除。 執行緒完成時顯示更新，它會藉由呼叫釋放 mutex `ReleaseMutex`。  
  
畫面會顯示和靜態資料的只有兩個需要審慎管理的資源。 例如，您的程式可能會有多個執行緒存取相同的檔案。 因為另一個執行緒可能已移動檔案指標，但是每個執行緒，必須重設之前讀取或寫入檔案指標。 此外，每個執行緒必須先確定不會佔用之間放置指標的時間和存取檔案的時間。 這些執行緒應該用來協調的方括號使用存取每個檔案的檔案的存取權的號誌`WaitForSingleObject`和`ReleaseMutex`呼叫。 下列程式碼範例說明這項技術：  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> 執行緒堆疊  
 
所有的應用程式的預設堆疊空間配置給第一個執行的執行緒，也就是執行緒 1。 如此一來，您必須指定需要多少記憶體配置個別針對每個額外的執行緒堆疊，因此您的程式。 作業系統會配置額外的堆疊空間的執行緒，如有必要，但您必須指定預設值。  
  
中的第一個引數`_beginthread`呼叫是一個指向`BounceProc`函式，它會執行的執行緒。 第二個引數會指定執行緒的預設堆疊大小。 最後一個引數是傳遞至 ID 號碼`BounceProc`。 `BounceProc` 使用識別碼來植入亂數產生器，並選取執行緒的色彩屬性和顯示的字元。  
  
C 執行階段程式庫或 Win32 API 進行呼叫的執行緒必須允許足夠的堆疊空間的程式庫和其所呼叫的 API 函式。 C`printf`函式需要超過 500 個位元組的堆疊空間，並呼叫 Win32 API 常式時，您應該有 2k 的堆疊空間可用。  
  
因為每個執行緒都有它自己的堆疊，可以使用為盡可能少的靜態資料，以避免透過資料的項目可能發生的衝突。 設計程式以使用自動堆疊變數可以是私用程式執行緒的所有資料。 只有全域程式內的變數 Bounce.c 是 mutex 或永遠不會變更後，變數會初始化的變數。  
  
Win32 也提供執行緒區域儲存區 (TLS) 來儲存每個執行緒資料。 如需詳細資訊，請參閱 <<c0> [ 執行緒區域儲存區 (TLS)](thread-local-storage-tls.md)。  
  
## <a name="see-also"></a>另請參閱  
 
[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)