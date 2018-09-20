---
title: 執行緒區域儲存區 (TLS) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6744fdd80e16e292399a261e10dc6b974af1dca4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371923"
---
# <a name="thread-local-storage-tls"></a>執行緒區域儲存區

執行緒區域儲存區 (Thread Local Storage，TLS) 是一種方法，讓指定之多執行緒處理序中的每個執行緒用來配置位置，以儲存執行緒特定資料。 動態繫結 (runtime) 執行緒專屬的資料透過 TLS API 支援 ([TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)。  除了現有的 API 實作以外，Win32 和 Visual C++ 編譯器現在支援靜態繫結 (載入時間) 的個別執行緒資料。

##  <a name="_core_compiler_implementation_for_tls"></a> TLS 的編譯器實作

**C + + 11:** `thread_local`儲存類別規範是建議用來指定物件的執行緒區域儲存區和類別成員。 如需詳細資訊，請參閱 <<c0> [ 儲存類別 （c + +）](../cpp/storage-classes-cpp.md)。

Visual c + + 也提供 Microsoft 特定屬性，[執行緒](../cpp/thread.md)，以擴充的儲存類別修飾詞。 使用 **__declspec**關鍵字來宣告**執行緒**變數。 例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>規則與限制

當您宣告靜態繫結的執行緒區域物件和變數時，必須遵守下列指導方針： 這些指導方針適用於兩者皆可[執行緒](../cpp/thread.md)並且大部分的情況下透過[thread_local](../cpp/storage-classes-cpp.md):

- **執行緒**屬性可以套用至類別和資料宣告和定義。 它不可使用於函式宣告或定義。 例如，下列程式碼會產生編譯器錯誤：

    ```
    __declspec( thread )void func();     // This will generate an error.
    ```

- **執行緒**可能只能在使用的資料項目上指定修飾詞**靜態**範圍。 這包括全域資料物件 (兩者**靜態**並**extern**)、 區域靜態物件和 c + + 類別的靜態資料成員。 自動資料物件不能以宣告**執行緒**屬性。 下列程式碼會產生編譯器錯誤：

    ```
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )    // This will generate an error.
    {
        return tls_i;
    }
    ```

- 宣告和定義都必須指定本機物件的執行緒**執行緒**屬性。 例如，下列程式碼會產生錯誤：

    ```
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- **執行緒**屬性不能做為類型修飾詞。 例如，下列程式碼會產生編譯器錯誤：

    ```
    char __declspec( thread ) *ch;        // Error
    ```

- 因為 c + + 宣告物件，使用**執行緒**允許屬性，下列兩個範例在語意上與：

    ```
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

- 執行緒區域物件的位址不會被視為常數，而且任何包含這種位址的運算式都不會被視為常數運算式。 在標準 C 中，其效果是禁止使用執行緒區域變數的位址做為物件或指標的初始設定式。 例如，C 編譯器會將下列程式碼標示為錯誤：

    ```
    __declspec( thread )int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

     這項限制不適用於 C++。 因為 C++ 允許所有物件的動態初始化，所以您可使用採用執行緒區域變數位址的運算式來初始化物件。 其完成方式就如同建構執行緒區域物件一樣。 例如，如果稍早所示的程式碼編譯為 C++ 原始程式檔，則不會產生錯誤。 請注意，只要採用執行緒區域變數位址的執行緒仍存在，此位址就有效。

- 標準 C 允許利用需要自我參考的運算式來初始化物件或變數，但只限於非靜態範圍的物件。 雖然 C++ 通常允利用需要自我參考的運算式來動態初始化對物件，但此種初始化不適用於執行緒區域物件。 例如: 

    ```
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

     請注意，包含所要初始化物件的 `sizeof` 運算式並不代表其本身的參考，但在 C 和 C++ 中皆已啟用。

     C++ 不允許執行緒資料的這類動態初始化，因為執行緒區域儲存區設備未來可能會增強。

- 在 Windows Vista 之前的 Windows 作業系統上`__declspec`(thread) 有一些限制。 如果 DLL 將任何資料或物件宣告為 `__declspec`(thread)，可能會造成保護錯誤 (若以動態方式載入)。 已載入 DLL 之後[LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)，它會導致系統失敗，每當程式碼參考`__declspec`(thread) 資料。 因為執行緒的全域變數空間是在執行階段進行配置，所以此空間的大小是以應用程式的需求，再加上以靜態方式連結之所有 DLL 的需求的計算為基礎。 當您使用 `LoadLibrary` 時，您無法擴充此空間以便使用 `__declspec`(thread) 宣告執行緒區域變數。 使用 TLS Api，例如[TlsAlloc](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-tlsalloc)，來配置 TLS，如果可能會使用載入的 DLL 在 DLL 中`LoadLibrary`。

## <a name="see-also"></a>另請參閱

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)