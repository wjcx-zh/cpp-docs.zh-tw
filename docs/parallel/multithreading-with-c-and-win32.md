---
title: 使用 C 和 Win32 進行多執行緒處理
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867049"
---
# <a name="multithreading-with-c-and-win32"></a>使用 C 和 Win32 進行多執行緒處理

Microsoft C/C++編譯器（MSVC）提供建立多執行緒應用程式的支援。 如果您的應用程式需要執行昂貴的作業，而導致使用者介面變成沒有回應，請考慮使用一個以上的執行緒。

使用 MSVC 時，有數種方式可以使用多個執行緒進行程式設計C++：您可以使用/WinRT 和 Windows 執行階段程式庫、Microsoft Foundation CLASS （MFC C++）程式庫、/cli 和 .net 執行時間，或 C 執行時間程式庫和 WIN32 API。 本文是關於 C 中的多執行緒處理。如需範例程式碼，請參閱[C 中的範例多執行緒程式](sample-multithread-c-program.md)。

## <a name="multithread-programs"></a>多執行緒程式

執行緒基本上是透過程式執行的路徑。 它也是 Win32 排定的最小執行單位。 執行緒是由堆疊、CPU 暫存器的狀態，以及系統排程器執行清單中的專案所組成。 每個執行緒都會共用所有進程的資源。

處理常式是由一個或多個執行緒，以及記憶體中程式的程式碼、資料和其他資源所組成。 一般的程式資源包括開啟的檔案、信號和動態配置的記憶體。 當系統排程器提供它的其中一個執行緒執行控制時，就會執行程式。 排程器會決定應該執行的執行緒，以及應該執行的時機。 較低優先順序的執行緒可能必須等待，較高優先順序的執行緒才能完成其工作。 在多處理器電腦上，排程器可以將個別執行緒移至不同的處理器，以平衡 CPU 負載。

進程中的每個執行緒都是獨立運作的。 除非您讓它們彼此可見，否則執行緒會個別執行，並不會察覺進程中的其他執行緒。 不過，共用一般資源的執行緒必須使用信號或處理序間通訊的另一種方法來協調其工作。 如需同步處理執行緒的詳細資訊，請參閱[撰寫多執行緒 Win32 程式](#writing-a-multithreaded-win32-program)。

## <a name="library-support-for-multithreading"></a>多執行緒的程式庫支援

所有版本的 CRT 現在都支援多執行緒，但某些函數的非鎖定版本除外。 如需詳細資訊，請參閱[多執行緒程式庫效能](../c-runtime-library/multithreaded-libraries-performance.md)。 如需可與您的程式碼連結之 CRT 版本的相關資訊，請參閱[crt 程式庫功能](../c-runtime-library/crt-library-features.md)。

## <a name="include-files-for-multithreading"></a>多執行緒的 Include 檔

標準 CRT include 檔案在程式庫中執行時，會宣告 C 執行時間程式庫函式。 如果您的編譯器選項指定[__fastcall 或 __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md)呼叫慣例，編譯器會假設應該使用註冊呼叫慣例來呼叫所有函式。 執行時間程式庫函式會使用 C 呼叫慣例，而標準 include 檔案中的宣告則會告知編譯器為這些函式產生正確的外部參考。

## <a name="crt-functions-for-thread-control"></a>Thread 控制項的 CRT 函式

所有 Win32 程式都至少有一個執行緒。 任何執行緒都可以建立額外的執行緒。 執行緒可以快速完成其工作，然後終止，也可以在程式的生命週期內保持使用中狀態。

CRT 程式庫提供下列函數來建立和終止執行緒： [_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)、 [_endthread 和 _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)。

`_beginthread` 和 `_beginthreadex` 函數會建立新的執行緒，並在作業成功時傳回執行緒識別碼。 執行緒會在完成執行時自動終止。 或者，它可以透過呼叫 `_endthread` 或 `_endthreadex`來自行終止。

> [!NOTE]
> 如果您從以 libcmt.lib 建立的程式呼叫 C 執行時間常式，就必須使用 `_beginthread` 或 `_beginthreadex` 函數來啟動您的執行緒。 請勿使用 Win32 函數 `ExitThread` 和 `CreateThread`。 當多個執行緒被封鎖，等候暫止的執行緒完成其對 C 執行時間資料結構的存取時，使用 `SuspendThread` 可能會導致鎖死。

### <a name="_core_the__beginthread_function"></a>_Beginthread 和 _beginthreadex 函數

`_beginthread` 和 `_beginthreadex` 函數會建立新的執行緒。 執行緒會與進程中的其他執行緒共用進程的程式碼和資料區段，但有它自己的唯一暫存器值、堆疊空間和目前的指令位址。 系統會提供 CPU 時間給每個執行緒，以便處理常式中的所有線程都可以同時執行。

`_beginthread` 和 `_beginthreadex` 類似于 WIN32 API 中的[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函式，但具有下列差異：

- 它們會初始化特定的 C 執行時間程式庫變數。 只有當您線上程中使用 C 執行時間程式庫時，這才是重要的。

- `CreateThread` 有助於提供安全性屬性的控制權。 您可以使用此函式來啟動處於已暫停狀態的執行緒。

`_beginthread` 和 `_beginthreadex` 會在成功時傳回新執行緒的控制碼，如果發生錯誤，則會傳回錯誤碼。

### <a name="_core_the__endthread_function"></a>_Endthread 和 _endthreadex 函數

[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md)函式會終止由 `_beginthread` 建立的執行緒（同樣地，`_endthreadex` 終止 `_beginthreadex`所建立的執行緒）。 執行緒完成時，會自動終止。 `_endthread` 和 `_endthreadex` 適用于執行緒內的條件式終止。 例如，專門用於通訊處理的執行緒若無法取得通訊埠的控制權，就可以結束。

## <a name="writing-a-multithreaded-win32-program"></a>撰寫多執行緒 Win32 程式

當您撰寫具有多個執行緒的程式時，您必須協調其行為和[程式資源的使用](#_core_sharing_common_resources_between_threads)。 此外，請確定每個執行緒都會接收[自己的堆疊](#_core_thread_stacks)。

### <a name="_core_sharing_common_resources_between_threads"></a>線上程之間共用一般資源

> [!NOTE]
> 如需 MFC 觀點的類似討論，請參閱[多執行緒：程式設計提示](multithreading-programming-tips.md)和[多執行緒：使用同步處理類別的](multithreading-when-to-use-the-synchronization-classes.md)時機。

每個執行緒都有自己的堆疊，以及它自己的 CPU 暫存器複本。 其他資源（例如檔案、靜態資料和堆積記憶體）會由進程中的所有線程共用。 使用這些通用資源的執行緒必須進行同步處理。 Win32 提供數種方式來同步處理資源，包括信號、關鍵區段、事件和 mutex。

當多個執行緒正在存取靜態資料時，您的程式必須提供可能的資源衝突。 請考慮一個程式，其中一個執行緒會更新靜態資料結構，其中包含要由另一個執行緒顯示之專案的*x*，*y*座標。 如果更新執行緒改變*x*座標，並在可以變更*y*座標之前先佔用，則顯示執行緒可能會在*y*座標更新之前排程。 專案會顯示在錯誤的位置。 您可以使用信號來控制結構的存取，以避免這個問題。

Mutex （short for *mut*ual *ex*clusion）是一種方式，可在彼此非同步執行的執行緒或進程之間進行通訊。 這項通訊可用來協調多個執行緒或進程的活動，通常是藉由鎖定和解除鎖定資源來控制對共用資源的存取。 為了解決這個*x*，*y*座標更新的問題，update 執行緒會設定 mutex，表示在執行更新之前，資料結構正在使用中。 這會在處理兩個座標後清除 mutex。 顯示執行緒必須等到 mutex 清除後，才能更新顯示。 這種等候 mutex 的程式通常稱為「mutex*封鎖*」，因為進程遭到封鎖，而且在 mutex 清除之前無法繼續執行。

[範例多執行緒 c 程式](sample-multithread-c-program.md)中顯示的彈跳程式會使用名為 `ScreenMutex` 的 mutex 來協調螢幕更新。 每當其中一個顯示執行緒準備好寫入畫面時，它會呼叫 `WaitForSingleObject`，其中包含 `ScreenMutex` 的控制碼，並使用無限的來表示 `WaitForSingleObject` 呼叫應該封鎖 mutex 而不會超時。如果 `ScreenMutex` 很清楚，wait 函式會設定 mutex，讓其他執行緒無法干擾顯示，並繼續執行執行緒。 否則，執行緒會封鎖，直到 mutex 清除為止。 當執行緒完成顯示更新時，它會藉由呼叫 `ReleaseMutex`來釋放 mutex。

畫面顯示，而靜態資料只是兩個需要謹慎管理的資源。 例如，您的程式可能會有多個執行緒存取相同的檔案。 因為另一個執行緒可能已移動檔案指標，所以每個執行緒必須先重設檔案指標，才能讀取或寫入。 此外，每個執行緒都必須確定它在放置指標的時間和存取檔案的時間之間不會被佔用。 這些執行緒應該使用信號來協調檔案的存取權，方法是使用 `WaitForSingleObject` 和 `ReleaseMutex` 呼叫來括弧每個檔案存取。 下列程式碼範例說明這項技術：

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>執行緒堆疊

所有應用程式的預設堆疊空間都會配置給第一個執行執行緒，也就是所謂的執行緒1。 因此，您必須針對程式所需的每個額外線程，指定配置給個別堆疊的記憶體數量。 如有需要，作業系統會為執行緒配置額外的堆疊空間，但您必須指定預設值。

`_beginthread` 呼叫中的第一個引數是 `BounceProc` 函式的指標，該函式會執行執行緒。 第二個引數會指定執行緒的預設堆疊大小。 最後一個引數是傳遞給 `BounceProc`的 ID 編號。 `BounceProc` 使用 ID 編號來植入亂數產生器，並選取執行緒的 color 屬性和顯示字元。

呼叫 C 執行時間程式庫或 WIN32 API 的執行緒，必須針對其所呼叫的程式庫和 API 函式，允許足夠的堆疊空間。 C `printf` 函式需要超過500個位元組的堆疊空間，而且在呼叫 WIN32 API 常式時，您應該有2K 個位元組的堆疊空間可用。

由於每個執行緒都有自己的堆疊，因此您可以使用最少的靜態資料來避免可能發生的資料項目目衝突。 設計您的程式，以針對可為執行緒私用的所有資料使用自動堆疊變數。 只有在初始化後，彈跳程式中的全域變數是不會變更的 mutex 或變數。

Win32 也提供執行緒區域儲存區（TLS）來儲存每個執行緒的資料。 如需詳細資訊，請參閱[執行緒區域儲存區（TLS）](thread-local-storage-tls.md)。

## <a name="avoiding-problem-areas-with-multithread-programs"></a>避免具有多執行緒程式的問題區域

建立、連結或執行多執行緒 C 程式時，您可能會遇到幾個問題。 下表說明一些較常見的問題。 （如需 MFC 觀點的類似討論，請參閱[多執行緒：程式設計提示](multithreading-programming-tips.md)）。

|問題|可能的原因|
|-------------|--------------------|
|您會看到一個訊息方塊，顯示您的程式造成保護違規。|許多 Win32 程式設計錯誤都會造成保護違規。 保護違規的常見原因是將資料間接指派給 null 指標。 因為這會導致您的程式嘗試存取不屬於它的記憶體，所以會發出保護違規。<br /><br /> 偵測保護違規原因的簡單方法，就是使用偵錯工具來編譯您的程式，然後在 Visual Studio 環境中透過偵錯工具來執行它。 當保護錯誤發生時，Windows 會將控制權轉移給偵錯工具，而游標會放在造成問題的那一行。|
|您的程式會產生許多編譯和連結錯誤。|您可以將編譯器的警告層級設定為其中一個最高的值，並不要再警告訊息，以排除許多潛在的問題。 藉由使用 [層級 3] 或 [層級 4] 警告層級選項，您可以偵測意外的資料轉換、遺漏函數原型，以及使用非 ANSI 功能。|

## <a name="see-also"></a>另請參閱

[舊版程式碼的多執行緒支援C++（Visual）](multithreading-support-for-older-code-visual-cpp.md)\
[C\ 中的範例多執行緒程式](sample-multithread-c-program.md)
[執行緒區域儲存區（TLS）](thread-local-storage-tls.md)\
[使用/WinRT\ 的C++並行和非同步作業](/windows/uwp/cpp-and-winrt-apis/concurrency)
[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
