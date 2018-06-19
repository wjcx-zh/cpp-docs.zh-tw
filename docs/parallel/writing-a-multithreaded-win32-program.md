---
title: 撰寫多執行緒的 Win32 程式 |Microsoft 文件
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
ms.openlocfilehash: 2d88add7830316ae192a728f9c9ff10320657eaf
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689970"
---
# <a name="writing-a-multithreaded-win32-program"></a>撰寫多執行緒 Win32 程式
當您撰寫多執行緒程式時，您必須協調其行為和[程式的資源的運用](#_core_sharing_common_resources_between_threads)。 您也必須確定每個執行緒會收到[自己的堆疊](#_core_thread_stacks)。  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> 一般執行緒之間共用資源  
  
> [!NOTE]
>  從 MFC 的觀點的類似討論，請參閱[多執行緒： 程式設計提示](../parallel/multithreading-programming-tips.md)和[多執行緒： 何時使用同步類別](../parallel/multithreading-when-to-use-the-synchronization-classes.md)。  
  
 每個執行緒有它自己的堆疊，以及各自的 CPU 暫存器。 其他資源，例如檔案、 靜態資料和堆積記憶體執行緒共用的所有處理序中。 使用這些常用的資源的執行緒必須同步處理。 Win32 提供數種方式可將資源，包括信號、 關鍵區段、 事件和 mutex 同步處理。  
  
 當多個執行緒同時存取靜態資料時，您的程式必須提供可能的資源衝突。 請考慮一個執行緒更新一個靜態資料結構，其中包含程式*x*，*y*座標的項目來顯示由另一個執行緒。 如果更新執行緒改變*x*協調與之前可能會變更為優先佔用*y*座標，顯示執行緒可能早*y*座標是更新。 此項目會顯示在錯誤的位置。 您可以使用信號控制結構的存取來避免這個問題。  
  
 Mutex (簡稱*里西斯 mut*ual *ex*clusion) 是一種執行緒或另一個以非同步方式執行的處理序之間進行通訊。 此通訊通常用來控制共用資源的存取權的鎖定和解除鎖定的資源通常協調多個執行緒或處理程序的活動。 若要解決此*x*，*y*座標更新問題，請更新執行緒設定 mutex，指示資料結構正在使用中，再執行更新。 它會清除 mutex 之後處理這兩個座標一樣。 顯示執行緒必須等待 mutex 更新顯示之前被清除。 這個程序的等候 mutex 通常稱為封鎖 mutex，因為處理序遭到封鎖，無法繼續，直到 mutex 清除。  
  
 Bounce.c 程式中顯示[多執行緒 C 程式範例](../parallel/sample-multithread-c-program.md)使用名為 mutex`ScreenMutex`協調更新螢幕。 它會呼叫其中一個顯示執行緒為準備好要寫入至畫面中，每次**WaitForSingleObject**的控制代碼與`ScreenMutex`和常數**無限**表示**WaitForSingleObject**呼叫應該要封鎖的 mutex 和逾時。如果`ScreenMutex`已取消選取，將 mutex，因此其他執行緒不會干擾顯示等候函式，並繼續執行執行緒。 否則，執行緒會封鎖，直到 mutex 清除。 當執行緒完成時顯示更新時，它會藉由呼叫釋放 mutex **ReleaseMutex**。  
  
 螢幕顯示和靜態資料是僅有兩種需要仔細的管理的資源。 例如，您的程式可能會有多個執行緒存取相同的檔案。 另一個執行緒可能已移動檔案指標，因為每個執行緒都必須重設的檔案指標設定，才能讀取或寫入。 此外，每個執行緒必須確定不會佔用的時間，它會將指標放到存取檔案的時間之間。 這些執行緒應該使用某個號誌的方括號與每個檔案存取協調檔案的存取權**WaitForSingleObject**和**ReleaseMutex**呼叫。 下列程式碼範例將說明這項技術：  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> 執行緒堆疊  
 所有的應用程式的預設堆疊空間配置給第一個執行的執行緒，也就是執行緒 1。 如此一來，您必須指定需要的記憶體數量，無法個別針對每個額外執行緒堆疊配置您的程式。 作業系統會配置額外的堆疊空間的執行緒，如有必要，但您必須指定預設值。  
  
 中的第一個引數`_beginthread`呼叫是指向**BounceProc**函式，以執行執行緒。 第二個引數會指定執行緒的預設堆疊大小。 最後一個引數會傳遞至一個識別碼**BounceProc**。 **BounceProc**使用識別碼來植入之隨機號碼產生器，並選取執行緒的色彩屬性和顯示的字元。  
  
 C 執行階段程式庫或 Win32 api 進行呼叫的執行緒必須允許足夠的堆疊空間程式庫和應用程式開發介面函式所呼叫。 C`printf`函式需要超過 500 個位元組的堆疊空間，而且呼叫 Win32 API 常式時，您應該已經 2k 堆疊可用的空間。  
  
 因為每個執行緒有它自己的堆疊，可以使用為盡可能少的靜態資料，以避免透過資料的項目發生衝突的可能性。 設計程式以使用自動堆疊變數可以是私人的執行緒的所有資料。 只有全域變數在 Bounce.c 程式係 mutex 或永遠不會變更後，變數會初始化的變數。  
  
 Win32 也提供執行緒區域儲存區 (TLS) 來儲存每個執行緒資料。 如需詳細資訊，請參閱[執行緒區域儲存區 (TLS)](../parallel/thread-local-storage-tls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)