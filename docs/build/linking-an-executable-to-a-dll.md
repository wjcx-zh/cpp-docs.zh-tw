---
title: 將可執行檔連結至 DLL
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: 2f907fedcaaf9897749ee0eb6a7ea5a33e1af679
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856822"
---
# <a name="link-an-executable-to-a-dll"></a>將可執行檔連結至 DLL

可執行檔會以下列兩種方式的其中一種連結至 DLL （或載入）：

- *隱含連結*，其中作業系統會在使用它的可執行檔時，同時載入 DLL。 用戶端可執行檔會呼叫 DLL 的匯出函式，就像是以靜態方式連結和包含在可執行檔中的函式一樣。 隱含連結有時稱為*靜態載入*或*載入時間動態連結*。

- *明確連結*，作業系統會在執行時間視需要載入 DLL。 透過明確連結使用 DLL 的可執行檔，必須明確地載入和卸載 DLL。 它也必須設定函式指標，以存取它從 DLL 使用的每個函式。 不同于靜態程式庫或隱含連結的 DLL 中函式的呼叫，用戶端可執行檔必須透過函式指標呼叫明確連結 DLL 中的匯出函數。 明確連結有時稱為*動態載入*或*執行時間動態連結*。

可執行檔可以使用任一連結方法來連結至相同的 DLL。 此外，這些方法不會互斥;一個可執行檔可以隱含地連結至 DLL，而另一個可以明確附加到它。

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>決定要使用哪一個連結方法

是否要使用隱含連結或明確連結，是您必須為應用程式進行的架構決策。 以上方法各有其優缺點。

### <a name="implicit-linking"></a>隱含連結

當應用程式的程式碼呼叫匯出的 DLL 函式時，就會發生隱含連結。 當編譯或組合呼叫可執行檔的原始程式碼時，DLL 函式呼叫會在物件程式碼中產生外部函數參考。 若要解決此外部參考，應用程式必須與 DLL 製作者所提供的匯入程式庫（.lib 檔案）連結。

匯入程式庫只包含載入 DLL 的程式碼，並在 DLL 中執行函式的呼叫。 在匯入程式庫中尋找外部函式，會通知連結器該函式的程式碼是在 DLL 中。 為了解析 Dll 的外部參考，連結器只會將資訊加入至可執行檔，告訴系統在處理常式啟動時，尋找 DLL 程式碼的位置。

當系統啟動包含動態連結參考的程式時，它會使用程式可執行檔中的資訊來尋找所需的 Dll。 如果找不到 DLL，系統就會終止進程，並顯示報告錯誤的對話方塊。 否則，系統會將 DLL 模組對應到進程位址空間。

如果有任何 Dll 具有初始化和終止程式碼（例如 `DllMain`）的進入點函式，作業系統就會呼叫函式。 傳遞至進入點函式的其中一個參數會指定程式碼，指出 DLL 正在附加至進程。 如果進入點函式未傳回 TRUE，則系統會終止進程並回報錯誤。

最後，系統會修改進程的可執行程式碼，以提供 DLL 函式的起始位址。

就像程式碼的其餘部分，載入器會在進程啟動時，將 DLL 程式碼對應到進程的位址空間。 作業系統只會在需要時將其載入記憶體。 因此，.def 檔案用來控制載入舊版 Windows 的 `PRELOAD` 和 `LOADONCALL` 程式碼屬性不再具有意義。

### <a name="explicit-linking"></a>明確連結

大部分的應用程式都會使用隱含連結，因為這是最容易使用的連結方法。 不過，有些時候需要明確連結。 以下是使用明確連結的一些常見原因：

- 應用程式不知道它載入的 DLL 名稱，直到執行時間為止。 例如，應用程式可能會在啟動時從設定檔案取得 DLL 的名稱和匯出的函式。

- 如果在進程啟動時找不到 DLL，作業系統就會終止使用隱含連結的進程。 在這種情況下，使用明確連結的進程並不會終止，而且可能會嘗試從錯誤中復原。 例如，處理常式可能會通知使用者錯誤，並讓使用者指定 DLL 的另一個路徑。

- 如果連結的任何 Dll 具有失敗的 `DllMain` 函式，則使用隱含連結的進程也會終止。 在這種情況下，不會終止使用明確連結的進程。

- 隱含連結至多個 Dll 的應用程式可能會很慢啟動，因為 Windows 會在應用程式載入時載入所有 Dll。 為了改善啟動效能，應用程式可能只會在載入之後立即針對需要的 Dll 使用隱含連結。 它可能會使用明確連結，只在需要時才載入其他 Dll。

- 明確連結可讓您不需要使用匯入程式庫來連結應用程式。 如果 DLL 中的變更導致匯出序數變更，則如果應用程式使用函式的名稱而不是序數值來呼叫 `GetProcAddress`，就不需要重新連結。 使用隱含連結的應用程式仍然必須重新連結到已變更的匯入程式庫。

以下是明確連結要注意的兩項風險：

- 如果 DLL 具有 `DllMain` 的進入點函式，作業系統會在呼叫 `LoadLibrary`的執行緒內容中呼叫函式。 如果 DLL 已附加至進程，而且先前呼叫的 `LoadLibrary` 沒有對應的 `FreeLibrary` 函式呼叫，則不會呼叫進入點函式。 如果 DLL 使用 `DllMain` 函式來初始化處理常式的每個執行緒，則明確連結可能會造成問題，因為呼叫 `LoadLibrary` （或 `AfxLoadLibrary`）時已經存在的任何執行緒並未初始化。

- 如果 DLL 將靜態範圍資料宣告為 `__declspec(thread)`，它可能會在明確連結時造成保護錯誤。 呼叫 `LoadLibrary`載入 DLL 之後，每當程式碼參考此資料時，就會造成保護錯誤。 （靜態範圍資料同時包含全域和本機靜態專案）。這就是為什麼當您建立 DLL 時，應該避免使用執行緒區域儲存區。 如果您無法這樣做，請告知 DLL 使用者動態載入 DLL 的潛在陷阱。 如需詳細資訊，請參閱[在動態連結程式庫中使用執行緒區域儲存區（Windows SDK）](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>如何使用隱含連結

若要透過隱含連結來使用 DLL，用戶端可執行檔必須從 DLL 的提供者取得這些檔案：

- 一或多個標頭檔（.h 檔案），其中包含 DLL 中匯出的資料、函式和C++類別的宣告。 DLL 所匯出的類別、函式和資料都必須標記為 `__declspec(dllimport)` 在標頭檔中。 如需詳細資訊，請參閱 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

- 要連結至可執行檔的匯入程式庫。 建立 DLL 時，連結器會建立匯入程式庫。 如需詳細資訊，請參閱[LIB 檔案做為連結器輸入](reference/dot-lib-files-as-linker-input.md)。

- 實際的 DLL 檔案。

若要透過隱含連結在 DLL 中使用資料、函式和類別，任何用戶端原始程式檔都必須包含宣告它們的標頭檔。 從編碼的觀點來看，對匯出函式的呼叫就像任何其他函式呼叫一樣。

若要建立用戶端可執行檔，您必須與 DLL 的匯入程式庫連結。 如果您使用外部 makefile 或組建系統，請同時指定匯入程式庫與其他物件檔案或您連結的文件庫。

作業系統必須能夠在載入呼叫可執行檔時找出 DLL 檔案。 這表示當您安裝應用程式時，您必須部署或驗證 DLL 是否存在。

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>如何明確連結至 DLL

若要透過明確連結來使用 DLL，應用程式必須進行函式呼叫，以便在執行時間明確載入 DLL。 若要明確連結到 DLL，應用程式必須：

- 呼叫[LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)或類似的函式，以載入 DLL 並取得模組控制碼。

- 呼叫[GetProcAddress](getprocaddress.md)以取得應用程式所呼叫之每個匯出函式的函式指標。 因為應用程式會透過指標呼叫 DLL 函式，所以編譯器不會產生外部參考，因此不需要與匯入程式庫連結。 不過，您必須擁有 `typedef` 或 `using` 語句，以定義所呼叫之匯出函式的呼叫簽章。

- 使用 DLL 完成時，請呼叫[FreeLibrary](freelibrary-and-afxfreelibrary.md) 。

例如，此範例函式會呼叫 `LoadLibrary` 來載入名為 "Mydll.dll" 的 DLL、呼叫 `GetProcAddress` 以取得名為 "DLLFunc1" 之函式的指標、呼叫函式並儲存結果，然後呼叫 `FreeLibrary` 以卸載 DLL。

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

與這個範例不同的是，在大多數情況下，您應該在應用程式中針對指定的 DLL 呼叫 `LoadLibrary` 並只 `FreeLibrary` 一次。 特別是如果您要在 DLL 中呼叫多個函式，或重複呼叫 DLL 函式。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [與匯入程式庫和匯出檔案一起使用](reference/working-with-import-libraries-and-export-files.md)

- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
