---
title: 執行緒區域儲存區
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: 888a33161cd33b20d5f40a07f9b54235f06b8bd8
ms.sourcegitcommit: 57e26bdd7839fce3c4154a61e987d165f0ba6f5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84301962"
---
# <a name="thread-local-storage-tls"></a>執行緒區域儲存區

執行緒區域儲存區 (Thread Local Storage，TLS) 是一種方法，讓指定之多執行緒處理序中的每個執行緒用來配置位置，以儲存執行緒特定資料。 TLS API （[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)）支援動態系結（執行時間）執行緒特定的資料。 除了現有的 API 執行，Win32 和 Microsoft c + + 編譯器現在還支援靜態系結（載入時間）每個執行緒的資料。

## <a name="compiler-implementation-for-tls"></a><a name="_core_compiler_implementation_for_tls"></a>TLS 的編譯器執行

**C + + 11：** `thread_local`儲存類別規範是針對物件和類別成員指定執行緒區域儲存區的建議方式。 如需詳細資訊，請參閱[儲存類別（c + +）](../cpp/storage-classes-cpp.md)。

MSVC 也會提供 Microsoft 專有的屬性（ [thread](../cpp/thread.md)）做為擴充儲存類別修飾詞。 使用 **__declspec**關鍵字來宣告**執行緒**變數。 例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>規則與限制

當您宣告靜態繫結的執行緒區域物件和變數時，必須遵守下列指導方針： 這些指導方針同時適用于[thread](../cpp/thread.md)和[thread_local](../cpp/storage-classes-cpp.md)：

- **Thread**屬性只能套用至類別和資料宣告和定義。 它不能用在函式宣告或定義上。 例如，下列程式碼會產生編譯器錯誤：

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- **執行緒**修飾詞只能在具有**靜態**範圍的資料項目上指定。 其中包括全域資料物件（**靜態**和**外部**）、本機靜態物件，以及 c + + 類別的靜態資料成員。 無法使用**thread**屬性來宣告自動資料物件。 下列程式碼會產生編譯器錯誤：

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- 執行緒區域物件的宣告和定義都必須指定**thread**屬性。 例如，下列程式碼會產生錯誤：

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **Thread**屬性不能當做類型修飾詞使用。 例如，下列程式碼會產生編譯器錯誤：

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- 由於允許使用**thread**屬性的 c + + 物件宣告，因此下列兩個範例在語義上是相等的：

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- 執行緒區域物件的位址不會被視為常數，而且任何牽涉到這類位址的運算式都不會被視為常數運算式。 在標準 C 中，效果是不允許使用執行緒區域變數的位址做為物件或指標的初始化運算式。 例如，C 編譯器會將下列程式碼標示為錯誤：

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   這項限制不適用於 c + +。 因為 C++ 允許所有物件的動態初始化，所以您可使用採用執行緒區域變數位址的運算式來初始化物件。 其做法就如同執行緒區域物件的結構一樣。 例如，稍早顯示的程式碼在編譯為 c + + 原始程式檔時，不會產生錯誤。 只有在已取得位址的執行緒仍然存在時，執行緒區域變數的位址才有效。

- 標準 C 允許使用牽涉到本身參考的運算式來初始化物件或變數，但僅適用于非靜態範圍的物件。 雖然 c + + 通常允許物件的動態初始化具有涉及本身參考的運算式，但這種初始化不允許用於執行緒區域物件。 例如：

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   `sizeof`包含所要初始化之物件的運算式不代表本身的參考，而且會同時在 c 和 c + + 中啟用。

   C + + 不允許對執行緒資料進行這類動態初始化，因為執行緒區域儲存設備的未來可能會有增強功能。

- 在 Windows Vista 之前的 Windows 作業系統上， `__declspec( thread )` 有一些限制。 如果 DLL 將任何資料或物件宣告為 `__declspec( thread )` ，它可能會在動態載入時造成保護錯誤。 使用[LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)載入 DLL 之後，每當程式碼參考資料時，就會導致系統失敗 `__declspec( thread )` 。 因為執行緒的全域變數空間是在執行階段進行配置，所以此空間的大小是以應用程式的需求，再加上以靜態方式連結之所有 DLL 的需求的計算為基礎。 當您使用時 `LoadLibrary` ，您無法擴充此空間，以允許使用所宣告的執行緒本機變數 `__declspec( thread )` 。 如果 DLL 可能會載入，請在您的 DLL 中使用 TLS Api （例如[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)）來配置 tls `LoadLibrary` 。

## <a name="see-also"></a>另請參閱

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)
