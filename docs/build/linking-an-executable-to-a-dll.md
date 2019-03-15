---
title: 連結至 DLL 的可執行檔
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
ms.openlocfilehash: fc7a676059af17e7a42189c7c15ca157a081e08a
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57818358"
---
# <a name="link-an-executable-to-a-dll"></a>連結至 DLL 的可執行檔

可執行檔連結至 （或載入） DLL 中有兩種：

- *隱含連結*，其中作業系統載入 DLL 時使用它的可執行檔載入時。 用戶端可執行檔呼叫的 dll 匯出的函式，就如同函式已靜態連結並包含在可執行檔。 隱含連結有時稱為*靜態負載*或是*載入時期動態連結*。

- *明確連結*，作業系統將視需要在執行階段 DLL 的載入位置。 明確連結，就會使用 DLL 的可執行檔必須製作明確載入和卸載 DLL，以及存取由 DLL 匯出函式的函式呼叫。 與靜態連結程式庫中的函式呼叫中，不同的可執行的用戶端必須透過函式指標的 DLL 中呼叫匯出的函式。 明確連結有時稱為*動態負載*或是*執行階段動態連結*。

可執行檔可以使用其中一個連結方法來連結至相同的 DLL。 此外，這些方法並不互斥。一個可執行檔可以隱含地連結至 DLL，以及另一個可以明確地連接到它。

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>連結至 DLL 的可執行檔

是否要使用隱含連結，或明確連結是您必須對您的應用程式的架構決策。 有優點和缺點，每個方法。

### <a name="implicit-linking"></a>隱含連結

應用程式的程式碼呼叫匯出的 DLL 函式時，就會發生隱含連結。 時呼叫的可執行檔的原始程式碼會編譯或組合，DLL 函式呼叫會產生物件程式碼中的外部函式參考。 若要解決這個外部參考，應用程式必須連結的 dll 製作者提供的匯入程式庫 （.lib 檔案）。

匯入程式庫只會包含程式碼載入的 DLL，並實作在 DLL 中的函式的呼叫。 在 匯入程式庫中尋找的外部函式，會通知連結器該函式的程式碼是在 DLL 中。 若要解決 Dll 的外部參考，連結器只是將資訊加入告知系統如何處理程序啟動時，找出 DLL 程式碼的可執行檔。

當系統啟動時啟動的程式包含動態連結的參考時，會使用資訊在程式的可執行檔來找出所需的 Dll。 如果它找不到所需的 DLL，系統就會終止處理序，並顯示報告錯誤的對話方塊。 否則，系統會將 DLL 模組對應至處理序的位址空間。

如果所有 Dll 具有初始化及終止程式碼的進入點函式，例如`DllMain`，作業系統會呼叫此函式。 其中一個參數傳遞給進入點函式指定的程式碼會指示該 DLL 附加至處理序。 如果進入點函式不會傳回 TRUE，系統就會終止處理序，並報告錯誤。

最後，系統會修改要提供的 DLL 函式的起始位址的處理序可執行的程式碼。

程式的程式碼的其餘部分，例如 DLL 程式碼會對應到處理序位址空間，當處理程序啟動，而且它會載入至記憶體，只在需要時。 如此一來，`PRELOAD`和`LOADONCALL`.def 檔，不會再載入舊版的 Windows 中的控制項所使用的程式碼屬性具有意義。

### <a name="explicit-linking"></a>明確連結

大部分的應用程式會使用隱含連結，因為它是要使用的最簡單的方式連結的方法。 不過，有一些明確連結時所需的時間。 以下是一些常見的原因，若要使用明確的連結：

- 應用程式不知道它會載入到執行階段 DLL 的名稱。 例如，應用程式可能會從組態檔啟動時取得 DLL 匯出的函式的名稱。

- 在處理序啟動時找不到 DLL 時，作業系統便會終止使用隱含連結的程序。 使用明確連結的程序並不會終止在此情況下，可以嘗試從錯誤復原。 例如，程序無法通知錯誤的使用者，並讓使用者指定 dll 的另一個路徑。

- 如果有任何的 Dll，它會連結至已使用隱含連結的程序也會終止`DllMain`函式，就會失敗。 使用明確連結的程序未在此情況下終止。

- 隱含連結至許多 Dll 的應用程式可以是慢而無法啟動，因為應用程式載入時，Windows 會載入所有 Dll。 若要改善啟動效能，應用程式隱含只能連結至這些 Dll 需要之後立即載入和等候，直到其他 Dll，才能明確地連結到它們。

- 明確連結，就不需要使用匯入程式庫連結應用程式。 如果在 DLL 中的變更會導致匯出序數，以變更，使用明確連結的應用程式就不必重新連結在呼叫`GetProcAddress`使用的函式，並不為序數的值，名稱，而使用隱含連結的應用程式必須重新連結新的匯入程式庫。

以下是要注意的明確連結的兩個處理的風險：

- 如果 DLL 有`DllMain`進入點函式，作業系統會呼叫此函式呼叫的執行緒內容中`LoadLibrary`。 如果 DLL 已經連結至處理程序因為前一個呼叫，不會呼叫進入點函式`LoadLibrary`，已沒有對應呼叫`FreeLibrary`函式。 明確連結可能會造成問題如果 DLL 使用`DllMain`函式來執行的處理程序的每個執行緒的初始設定，因為執行緒已存在時`LoadLibrary`(或`AfxLoadLibrary`) 稱為未初始化。

- 如果 DLL 宣告靜態範圍的資料，做為`__declspec(thread)`，如果明確連結，它可能會造成保護錯誤。 藉由呼叫載入 DLL 之後`LoadLibrary`，它會造成保護錯誤，每當程式碼會參考此資料。 （靜態範圍的資料包括全域和區域靜態的項目）。因此，當您建立 DLL 時，您應該避免使用執行緒區域儲存區或告知 DLL 使用者有潛在的問題，以動態方式載入您的 DLL。 如需詳細資訊，請參閱 <<c0> [ 動態連結程式庫 (Windows SDK) 中使用執行緒區域儲存區](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library)。

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>連結至 DLL 的可執行檔

若要使用的隱含連結的 DLL，用戶端可執行檔必須從該 DLL 的提供者取得這些檔案：

- 一或多個標頭檔 （.h 檔案） 包含匯出的資料、 函數和/或 DLL 中的 c + + 類別的宣告。 類別、 函式，以及由 DLL 匯出的資料必須全部標示為`__declspec(dllimport)`標頭檔。 如需詳細資訊，請參閱 < [dllexport、 dllimport](../cpp/dllexport-dllimport.md)。

- 若要連結到可執行檔匯入程式庫。 建置 DLL 時，連結器會建立匯入程式庫。 如需詳細資訊，請參閱[。LIB 檔案](reference/dot-lib-files-as-linker-input.md)。

- 實際的 DLL 檔案。

若要使用的隱含連結的 DLL，可執行檔必須包含宣告的資料、 函數或匯出的 DLL 中包含匯出的資料、 函數和類別的呼叫每個原始程式檔的 c + + 類別的標頭檔。 從程式碼撰寫的觀點來看，匯出的函式呼叫會如同其他任何函式呼叫。

若要建置呼叫的可執行檔，您必須連結到匯入程式庫。 如果您使用外部 makefile，或建置系統，請指定您用來列出其他物件 (.obj) 檔案匯入程式庫或程式庫，您將連結的檔案名稱。

作業系統必須能夠載入呼叫的可執行檔時，找出 DLL 檔案。 這表示您的應用程式必須部署，或安裝您的應用程式時，請確認 DLL 存在。

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>如何明確地連結至 DLL

若要使用的明確連結的 DLL，應用程式必須進行明確地在執行階段載入的 DLL 呼叫的函式。 若要明確地連結至 DLL，應用程式必須：

- 呼叫[LoadLibrary](loadlibrary-and-afxloadlibrary.md)， `LoadLibraryEx`，或類似的函式，來載入的 DLL，並取得模組控制代碼。

- 呼叫[GetProcAddress](getprocaddress.md)取得函式指標至每個匯出的應用程式呼叫的函式。 應用程式呼叫 DLL 函式透過指標，因為編譯器不會產生外部參考，因此不需要連結匯入程式庫。 不過，您必須擁有`typedef`或`using`定義匯出的函式所呼叫的呼叫簽章的陳述式。

- 呼叫[FreeLibrary](freelibrary-and-afxfreelibrary.md) dll 所完成。

例如，此範例函式呼叫`LoadLibrary`若要載入 DLL，名為"MyDLL 」，會呼叫`GetProcAddress`來取得名為"DLLFunc1 」，函式的指標呼叫函式並儲存結果，然後再呼叫`FreeLibrary`卸載 DLL。

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

不同於在此範例中，在大部分情況下您應該呼叫`LoadLibrary`和`FreeLibrary`重複一次在您的應用程式，為指定的 dll，請特別是如果您要呼叫的 DLL 中的多個函式或呼叫 DLL 函式。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [與匯入程式庫和匯出檔案一起使用](reference/working-with-import-libraries-and-export-files.md)

- [動態連結程式庫搜尋順序](/windows/desktop/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>另請參閱

[Visual C++ 中的 DLL](dlls-in-visual-cpp.md)
