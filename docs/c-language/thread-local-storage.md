---
title: 執行緒區域儲存區
ms.date: 11/04/2016
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
ms.openlocfilehash: e13aa9600cd26fba47ce43a318fa7174995d58fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572220"
---
# <a name="thread-local-storage"></a>執行緒區域儲存區

**Microsoft 專屬**

執行緒區域儲存區 (Thread Local Storage，TLS) 是一種機制，讓指定之多執行緒處理序中的每個執行緒用來配置儲存區，以儲存執行緒特定資料。 在標準多執行緒程式中，資料是在特定處理序的所有執行緒之間共用，而執行緒區域儲存區則是用於配置每個執行緒資料的機制。 如需執行緒的完整討論，請參閱 Windows SDK 中的[處理序與執行緒](/windows/desktop/ProcThread/processes-and-threads)。

Microsoft C 語言包括擴充儲存類別屬性 thread，可搭配 __declspec 關鍵字宣告執行緒區域變數。 例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```
__declspec( thread ) int tls_i = 1;
```

當您宣告靜態繫結的執行緒區域變數時，必須遵守下列方針：

- 具有動態初始化的執行緒區域變數只會在使 DLL 載入的執行緒和已在處理序中執行的執行緒上初始化。 如需詳細資訊，請參閱[執行緒](../cpp/thread.md)。

- 您只能將 thread 屬性套用至資料宣告和定義。 它不可使用於函式宣告或定義。 例如，下列程式碼會產生編譯器錯誤：

    ```C
    #define Thread   __declspec( thread )
    Thread void func();      /* Error */
    ```

- 您只能在具有靜態儲存期的資料項目上指定 thread 屬性。 這包括全域資料 (同時包含 static 和 extern) 和區域靜態資料。 您無法使用 thread 屬性宣告自動資料。 例如，下列程式碼會產生編譯器錯誤：

    ```C
    #define Thread   __declspec( thread )
    void func1()
    {
        Thread int tls_i;            /* Error */
    }

    int func2( Thread int tls_i )    /* Error */
    {
       return tls_i;
    }
    ```

- 不論宣告和定義是發生在相同的檔案還是不同的檔案中，您都必須使用 thread 屬性宣告和定義執行緒區域資料。 例如，下列程式碼會產生錯誤：

    ```C
    #define Thread   __declspec( thread )
    extern int tls_i;     /* This generates an error, because the   */
    int Thread tls_i;     /* declaration and the definition differ. */
    ```

- 您無法使用 thread 屬性做為類型修飾詞。 例如，下列程式碼會產生編譯器錯誤：

    ```C
    char *ch __declspec( thread );      /* Error */
    ```

- 執行緒區域變數的位址不會被視為常數，而且任何牽涉到此類位址的運算式都不會被視為常數運算式。 這表示，您無法使用執行緒區域變數的位址做為指標的初始設定式。 例如，編譯器會將下列程式碼標示為錯誤：

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i;
    int *p = &tls_i;      /* Error */
    ```

- C 允許使用需要自我參考的運算式來初始化變數，但只限於非靜態範圍的物件。 例如: 

    ```C
    #define Thread   __declspec( thread )
    Thread int tls_i = tls_i;             /* Error */
    int j = j;                            /* Error */
    Thread int tls_i = sizeof( tls_i )    /* Okay  */
    ```

   請注意，包含要初始化之變數的 sizeof 運算式並不會構成其本身的參考，因此可以使用。

- 使用 **__declspec(thread)** 可能會干擾 DLL 匯入的[延遲載入](../build/reference/linker-support-for-delay-loaded-dlls.md)**。**

如需使用 thread 屬性的詳細資訊，請參閱[多執行緒主題](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)