---
title: 將可執行檔連結至 DLL
ms.date: 11/04/2016
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
ms.openlocfilehash: c4f9ea7a3606612189e85401b75a0577896fd90e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493230"
---
# <a name="link-an-executable-to-a-dll"></a>將可執行檔連結至 DLL

可執行檔會以下列兩種方式的其中一種連結至 DLL (或載入):

- *隱含連結*, 其中作業系統會在載入使用它的可執行檔時載入 DLL。 用戶端可執行檔會呼叫 DLL 的匯出函式, 就像函式是以靜態方式連結並包含在可執行檔中。 隱含連結有時稱為*靜態載入*或*載入時間動態連結*。

- *明確連結*, 作業系統會在執行時間視需要載入 DLL。 透過明確連結使用 DLL 的可執行檔必須進行函式呼叫, 以明確載入和卸載 DLL, 並存取 DLL 匯出的函式。 不同于靜態程式庫中的函式呼叫, 用戶端可執行檔必須透過函式指標呼叫 DLL 中匯出的函式。 明確連結有時稱為*動態載入*或*執行時間動態連結*。

可執行檔可以使用任一連結方法來連結至相同的 DLL。 此外, 這些方法並不是互斥的;一個可執行檔可以隱含地連結至 DLL, 而另一個可以明確附加到它。

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>將可執行檔連結至 DLL

是否要使用隱含連結或明確連結, 是您必須為應用程式進行的架構決策。 每種方法都有其優點和缺點。

### <a name="implicit-linking"></a>隱含連結

當應用程式的程式碼呼叫匯出的 DLL 函式時, 就會發生隱含連結。 當編譯或組合呼叫可執行檔的原始程式碼時, DLL 函式呼叫會在物件程式碼中產生外部函數參考。 若要解決此外部參考, 應用程式必須與 DLL 製作者所提供的匯入程式庫 (.lib 檔案) 連結。

匯入程式庫只包含載入 DLL 的程式碼, 並在 DLL 中執行函式的呼叫。 在匯入程式庫中尋找外部函式, 會通知連結器該函式的程式碼是在 DLL 中。 為了解析 Dll 的外部參考, 連結器只會將資訊加入至可執行檔, 告訴系統在處理常式啟動時, 尋找 DLL 程式碼的位置。

當系統啟動包含動態連結參考的程式時, 它會使用程式可執行檔中的資訊來尋找所需的 Dll。 如果找不到 DLL, 系統就會終止進程, 並顯示報告錯誤的對話方塊。 否則, 系統會將 DLL 模組對應至處理常式的位址空間。

如果有任何 dll 具有初始化和終止程式碼 (例如`DllMain`) 的進入點函式, 作業系統就會呼叫函數。 傳遞至進入點函式的其中一個參數會指定程式碼, 指出 DLL 正在附加至進程。 如果進入點函式未傳回 TRUE, 則系統會終止進程並回報錯誤。

最後, 系統會修改進程的可執行程式碼, 以提供 DLL 函式的起始位址。

就像程式碼的其餘部分, DLL 程式碼會在進程啟動時對應至進程的位址空間, 而且只有在需要時才會載入記憶體中。 因此, .def 檔案用`PRELOAD`來`LOADONCALL`控制載入舊版 Windows 的和程式碼屬性不再具有意義。

### <a name="explicit-linking"></a>明確連結

大部分的應用程式都會使用隱含連結, 因為它是最簡單的連結方法。 不過, 有些時候需要明確連結。 以下是使用明確連結的一些常見原因:

- 應用程式不知道它載入的 DLL 名稱, 直到執行時間為止。 例如, 應用程式可能會在啟動時從設定檔案取得 DLL 的名稱和匯出的函式。

- 如果在進程啟動時找不到 DLL, 則作業系統會終止使用隱含連結的進程。 在此情況下, 使用明確連結的進程並不會終止, 而且可能會嘗試從錯誤中復原。 例如, 處理常式可能會通知使用者錯誤, 並讓使用者指定 DLL 的另一個路徑。

- 如果連結的任何 dll 具有`DllMain`失敗的函式, 則使用隱含連結的進程也會終止。 在此情況下, 使用明確連結的進程並不會終止。

- 隱含連結至多個 Dll 的應用程式可能會很慢啟動, 因為 Windows 會在應用程式載入時載入所有 Dll。 為了改善啟動效能, 應用程式只能隱含地連結至載入後立即需要的 Dll, 並等候其他 Dll 明確連結它們。

- 明確連結可讓您不需要使用匯入程式庫來連結應用程式。 如果 DLL 中的變更導致匯出序數變更, 則使用明確連結的應用程式不需要重新連結, 如果它們是`GetProcAddress`使用函式的名稱而不是序數值來呼叫, 而使用隱含連結的應用程式則必須重新連結至新增匯入程式庫。

以下是明確連結要注意的兩項風險:

- 如果 DLL 具有`DllMain`進入點函式, 作業系統`LoadLibrary`會在呼叫的執行緒內容中呼叫函式。 如果 DLL 已附加至進程, 而且先前的呼叫對`LoadLibrary`函式沒有任何對應的呼叫`FreeLibrary` , 則不會呼叫該進入點函式。 如果 DLL 使用`DllMain`函式來執行進程中每個執行緒的初始化作業, 則明確連結可能會造成問題, 因為呼叫`LoadLibrary` (或`AfxLoadLibrary`) 時已經存在的執行緒並未初始化。

- 如果 DLL 將靜態範圍資料宣告為`__declspec(thread)`, 它可能會在明確連結時造成保護錯誤。 呼叫載入 DLL 之後`LoadLibrary`, 每當程式碼參考此資料時, 就會造成保護錯誤。 (靜態範圍資料同時包含全域和本機靜態專案)。因此, 當您建立 DLL 時, 您應該避免使用執行緒區域儲存區, 或通知 DLL 使用者動態載入 DLL 的可能錯誤。 如需詳細資訊, 請參閱[在動態連結程式庫中使用執行緒區域儲存區 (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>將可執行檔連結至 DLL

若要透過隱含連結來使用 DLL, 用戶端可執行檔必須從 DLL 的提供者取得這些檔案:

- 一或多個標頭檔 (.h 檔案), 其中包含 DLL 中匯出的資料、函式和 ( C++或) 類別的宣告。 DLL 所匯出的類別、函式和資料都必須全部標記`__declspec(dllimport)`在標頭檔中。 如需詳細資訊，請參閱 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。

- 要連結至可執行檔的匯入程式庫。 建立 DLL 時, 連結器會建立匯入程式庫。 如需詳細資訊, 請參閱[。LIB](reference/dot-lib-files-as-linker-input.md)檔案。

- 實際的 DLL 檔案。

若要透過隱含連結來使用 DLL, 可執行檔必須包含標頭檔案, 這些檔案會宣告C++每個原始程式檔中的 DLL 所匯出的資料、函式或類別, 其中包含對匯出資料、函式和類別的呼叫。 從編碼的觀點來看, 對匯出函式的呼叫就像任何其他函式呼叫一樣。

若要建立呼叫的可執行檔, 您必須與匯入程式庫連結。 如果您使用外部 makefile 或組建系統, 請指定匯入程式庫的檔案名, 其中列出您要連結的其他物件 (.obj) 檔案或文件庫。

作業系統必須能夠在載入呼叫可執行檔時找出 DLL 檔案。 這表示當您的應用程式安裝時, 您的應用程式必須部署或驗證 DLL 是否存在。

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>如何明確連結至 DLL

若要透過明確連結來使用 DLL, 應用程式必須進行函式呼叫, 以便在執行時間明確載入 DLL。 若要明確連結到 DLL, 應用程式必須:

- 呼叫[LoadLibrary](loadlibrary-and-afxloadlibrary.md)、 `LoadLibraryEx`或類似的函式, 以載入 DLL 並取得模組控制碼。

- 呼叫[GetProcAddress](getprocaddress.md)以取得應用程式所呼叫之每個匯出函式的函式指標。 因為應用程式會透過指標呼叫 DLL 函式, 所以編譯器不會產生外部參考, 因此不需要與匯入程式庫連結。 不過, 您必須擁有`typedef`或`using`語句, 以定義所呼叫之匯出函式的呼叫簽章。

- 使用 DLL 完成時, 請呼叫[FreeLibrary](freelibrary-and-afxfreelibrary.md) 。

例如, 此範例函式會`LoadLibrary`呼叫以載入名為 "mydll.dll" 的 DLL `GetProcAddress` , 呼叫以取得名為 "DLLFunc1" 之函式的指標, 呼叫函式並儲存結果, 然後`FreeLibrary`呼叫以卸載 DLL。

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

不同于在此範例中, 在大多數情況下`LoadLibrary` , `FreeLibrary`您應該只在應用程式中針對指定的 DLL 呼叫一次, 特別是如果您要在 DLL 中呼叫多個函式, 或重複呼叫 dll 函式。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [與匯入程式庫和匯出檔案一起使用](reference/working-with-import-libraries-and-export-files.md)

- [動態連結程式庫搜尋順序](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>另請參閱

[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
