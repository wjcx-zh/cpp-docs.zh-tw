---
title: "連結到 DLL 的可執行檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6bdc8d4b372a589beb51d2f8a9bc05b1aa241c48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="link-an-executable-to-a-dll"></a>可執行檔連結至 DLL  
  
可執行檔連結至 （或載入） DLL 中有兩種：  
  
-   *隱含連結*，其中作業系統載入 DLL 時使用它的可執行檔載入時。 用戶端可執行檔呼叫的 dll 匯出的函式，就如同函式是以靜態方式連結，並包含在可執行檔。 隱含連結有時稱為*靜態載入*或*載入時間動態連結*。  
  
-   *明確連結*，作業系統將視需要執行階段於 DLL 的載入位置。 藉由明確連結使用 DLL 的可執行檔必須進行明確載入和卸載 DLL，以及存取由 DLL 匯出的函式的函式呼叫。 不同於以靜態方式連結的程式庫中的函式的呼叫，可執行用戶端必須透過函式指標在 DLL 中呼叫匯出的函式。 明確連結有時稱為*動態負載*或*執行階段動態連結*。  
  
可執行檔可以使用任一連結的方法來連結至相同的 DLL。 此外，這些方法不會互斥。一個可執行檔可以隱含地連結到 DLL 和另一個可以明確地附加至這個。  
  
<a name="determining-which-linking-method-to-use"></a>  
  
## <a name="determine-which-linking-method-to-use"></a>決定要使用哪一個連結方法  
  
是否要使用連結的隱含或明確連結是您必須對您的應用程式的架構決策。 有一些優點和缺點，每個方法。  
  
### <a name="implicit-linking"></a>隱含連結  
  
應用程式的程式碼呼叫匯出的 DLL 函式時，就會發生隱含連結。 時呼叫的可執行檔的程式碼會編譯，或組合，DLL 函式呼叫會產生物件程式碼中的外部函式參考。 若要解決這種外部參考，應用程式必須連結的 DLL 所提供的匯入程式庫 （.lib 檔案）。  
  
匯入程式庫只包含程式碼載入的 DLL，並實作在 DLL 中函式的呼叫。 在匯入程式庫中尋找的外部函式，會通知連結器該函式的程式碼是在 DLL 中。 若要解決 Dll 的外部參考，連結器只是將資訊加入告訴系統如何尋找處理程序啟動時的 DLL 程式碼的可執行檔。  
  
當系統啟動時包含動態連結的參考的程式時，它會使用資訊程式的可執行檔中找出所需的 Dll。 如果找不到 DLL，系統就會終止處理序，並顯示對話方塊報告錯誤。 否則，系統會將 DLL 模組對應至處理序的位址空間。  
  
必須有的任何 Dll 初始化及終止程式碼的進入點函式例如`DllMain`，作業系統會呼叫此函式。 其中一個參數傳遞至進入點函式指定的程式碼會指示該 DLL 附加至處理序。 如果進入點函式不會傳回 TRUE，系統就會終止處理序，並報告錯誤。  
  
最後，系統會修改要提供 DLL 函式的起始位址的處理序可執行的程式碼。  
  
程式的程式碼的其餘部分，例如 DLL 程式碼會對應到處理序的位址空間，當處理序啟動並載入記憶體，僅在需要時。 如此一來，`PRELOAD`和`LOADONCALL`.def 檔案，不會再載入舊版的 Windows 控制項所使用的程式碼屬性具有意義。  
  
### <a name="explicit-linking"></a>明確連結  
  
大部分的應用程式會使用隱含連結，因為它是容易使用的連結要使用的方法。 不過，有明確連結時所需的時間。 以下是一些常見的原因，若要使用明確的連結：  
  
-   應用程式不知道它會等到執行階段載入的 dll 名稱。 例如，應用程式可能會從組態檔，啟動取得 DLL 匯出的函式的名稱。  
  
-   如果在處理序啟動時找不到 DLL，作業系統便會終止使用隱含連結的處理序。 使用明確連結的處理序並不會終止在此情況下，可以嘗試從錯誤中復原。 例如，程序無法通知錯誤的使用者，並讓使用者指定的 DLL 的另一個路徑。  
  
-   如果的任何 Dll，它會連結至已使用隱含連結的處理序也會終止`DllMain`函式，就會失敗。 使用明確連結的處理序未在此情況下結束。  
  
-   隱含連結至多 Dll 應用程式可以是慢而無法啟動，因為應用程式載入時，Windows 會載入所有 Dll。 若要改善啟動效能，應用程式可以隱含地只連結至這些 Dll，需要之後立即載入與等候，直到明確連結到他們所需的其他 Dll。  
  
-   明確連結不需要使用匯入程式庫連結應用程式。 如果在 DLL 中的變更會造成匯出序數變更，使用明確連結的應用程式不必重新連結，如果它們呼叫`GetProcAddress`使用函式並不是序數值的名稱，而使用隱含連結的應用程式必須重新連結新匯入程式庫。  
  
以下是要注意的明確連結的兩個風險：  
  
-   如果 dll`DllMain`進入點函式，作業系統會呼叫此函式呼叫的執行緒內容中`LoadLibrary`。 如果 DLL 已附加至處理序因為先前呼叫的進入點函式不會呼叫`LoadLibrary`，已經不需要對應呼叫`FreeLibrary`函式。 明確連結可能會造成問題如果 DLL 使用`DllMain`函式來執行的處理序的每個執行緒的初始設定，因為執行緒已存在時`LoadLibrary`(或`AfxLoadLibrary`) 稱為未初始化。  
  
-   如果 DLL 宣告靜態範圍的資料，做為`__declspec(thread)`，它可能造成保護錯誤，如果明確地連結。 藉由呼叫載入 DLL 之後`LoadLibrary`，它會造成保護錯誤，每當程式碼會參考此資料。 （靜態範圍的資料包括全域和區域靜態項目）。因此，當您建立 DLL，您應該避免使用執行緒區域儲存區或告知 DLL 使用者相關的動態載入您的 DLL 潛在的問題。 如需詳細資訊，請參閱[動態連結程式庫 (Windows SDK) 中使用執行緒區域儲存區](http://msdn.microsoft.com/library/windows/desktop/ms686997)。  
  
<a name="linking-implicitly"></a>  
  
## <a name="how-to-link-implicitly-to-a-dll"></a>如何以隱含方式連結到 DLL  
  
若要使用隱含連結的 DLL，用戶端可執行檔必須從該 DLL 的提供者取得這些檔案：  
  
-   一或多個標頭檔 （.h 檔案） 包含匯出的資料、 函數及/或 DLL 中的 c + + 類別的宣告。 類別、 函式，以及由 DLL 匯出的資料必須全部標示`__declspec(dllimport)`標頭檔中。 如需詳細資訊，請參閱[dllexport、 dllimport](../cpp/dllexport-dllimport.md)。  
  
-   若要連結到可執行檔匯入程式庫。 建置 DLL 時，連結器會建立匯入程式庫。 如需詳細資訊，請參閱[。LIB 檔案](../build/reference/dot-lib-files-as-linker-input.md)。  
  
-   實際的 DLL 檔案。  
  
若要使用隱含連結的 DLL，可執行檔必須包含宣告的資料、 函數或匯出的每個原始程式檔，其中包含要匯出的資料、 函數和類別的呼叫 DLL 的 c + + 類別的標頭檔。 程式碼撰寫的觀點而言，匯出的函式的呼叫就像其他任何函式呼叫。  
  
若要建置呼叫的可執行檔，您必須匯入程式庫連結。 如果您使用外部 makefile 或建置系統時，指定您用來列出其他的 (.obj) 檔案匯入程式庫或您所連結的媒體櫃的檔案名稱。  
  
作業系統必須是能夠載入呼叫的可執行檔時，找出 DLL 檔案。 這表示您的應用程式必須部署或安裝您的應用程式時，請確認 DLL 存在。   
  
<a name="linking-explicitly"></a>  
  
## <a name="how-to-link-explicitly-to-a-dll"></a>如何明確地連結到 DLL  
  
若要使用由明確連結的 DLL，應用程式必須進行明確執行階段載入的 DLL 呼叫的函式。 若要明確地連結到 DLL，應用程式必須：  
  
-   呼叫[LoadLibrary](loadlibrary-and-afxloadlibrary.md)， `LoadLibraryEx`，或類似的函式，來載入的 DLL，並取得模組控制代碼。  
  
-   呼叫[GetProcAddress](getprocaddress.md)取得函式指標至每個匯出的應用程式呼叫的函式。 應用程式呼叫 DLL 函式透過指標，因為編譯器不會產生外部參考，因此不需要匯入程式庫連結。 不過，您必須擁有`typedef`或`using`定義匯出的函式所呼叫的呼叫簽章的陳述式。   
  
-   呼叫[FreeLibrary](freelibrary-and-afxfreelibrary.md)時使用的 DLL 完成。  
  
例如，此範例函式呼叫`LoadLibrary`載入名為"MyDLL"，DLL 會呼叫`GetProcAddress`取得名為"DLLFunc1 」，函式的指標呼叫函式並儲存結果，然後再呼叫`FreeLibrary`卸載 DLL。 
  
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
  
不同於在此範例中，在大部分情況下您應該呼叫`LoadLibrary`和`FreeLibrary`重複一次針對指定的 DLL，特別是如果您要呼叫 DLL 中的多個函式或呼叫 DLL 應用程式中函式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [與匯入程式庫和匯出檔案一起使用](../build/reference/working-with-import-libraries-and-export-files.md)  
  
-   [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)