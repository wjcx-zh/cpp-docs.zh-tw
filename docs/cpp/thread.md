---
title: 執行緒
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 13e6d45642c08a97c06d7099b83e632501267310
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225809"
---
# <a name="thread"></a>執行緒

**Microsoft 特定的**

**`thread`** 擴充儲存類別修飾詞是用來宣告執行緒區域變數。 如需 c + + 11 和更新版本中的可移植對等用法，請使用可移植程式碼的[thread_local](../cpp/storage-classes-cpp.md#thread_local)儲存類別規範。 Windows 上的 **`thread_local`** 會使用來執行 **`__declspec(thread)`** 。

## <a name="syntax"></a>語法

**`__declspec(thread)`***declarator*宣告子

## <a name="remarks"></a>備註

執行緒區域儲存區 (Thread Local Storage，TLS) 是一種機制，讓多執行緒處理序中的每個執行緒用來配置儲存區，以儲存執行緒特定資料。 在標準多執行緒程式中，資料是在特定處理序的所有執行緒之間共用，而執行緒區域儲存區則是用於配置每個執行緒資料的機制。 如需執行緒的完整討論，請參閱[多執行緒](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

執行緒區域變數的宣告必須使用[擴充屬性語法](../cpp/declspec.md)和關鍵字搭配 **`__declspec`** **`thread`** 關鍵字。 例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```cpp
__declspec( thread ) int tls_i = 1;
```

在動態載入的程式庫中使用執行緒區域變數時，您必須留意可能導致執行緒區域變數無法正確初始化的因素：

1. 如果變數是使用函式呼叫（包括函式）進行初始化，則只會針對導致二進位/DLL 載入進程的執行緒，以及在載入二進位/DLL 之後啟動的執行緒呼叫此函數。 載入 DLL 時，任何已執行的其他執行緒都不會呼叫初始化函數。 動態初始化會在 DLL_THREAD_ATTACH 的 DllMain 呼叫上進行，但是如果 DLL 線上程啟動時不在進程中，則 DLL 永遠不會取得該訊息。

1. 使用常數值以靜態方式初始化的執行緒區域變數，通常會在所有線程上正確地初始化。 不過，從2017年12月起，Microsoft c + + 編譯器中有已知的一致性問題， **`constexpr`** 而變數會接收動態而非靜態初始化。

   注意：在未來的編譯器更新中，這兩個問題都應該是固定的。

此外，在宣告執行緒區域物件和變數時，您必須遵守下列方針：

- 您 **`thread`** 只能將屬性套用至類別和資料宣告和定義; **`thread`** 不能用在函式宣告或定義上。

- 您 **`thread`** 只能在具有靜態儲存期的資料項目上指定屬性。 這包括全域資料物件（ **`static`** 和 **`extern`** ）、本機靜態物件，以及類別的靜態資料成員。 您無法使用屬性來宣告自動資料物件 **`thread`** 。

- **`thread`** 不論宣告和定義發生在相同的檔案還是不同的檔案中，您都必須將屬性用於執行緒區域物件的宣告和定義。

- 您不能使用 **`thread`** 屬性做為型別修飾詞。

- 因為允許使用屬性的物件宣告 **`thread`** ，所以這兩個範例在語義上是相等的：

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- 標準 C 允許將物件或變數初始化為涉及本身參考的運算式，但僅適用于非靜態物件。 雖然 c + + 通常允許物件的這類動態初始化具有涉及本身參考的運算式，但這種初始化不允許用於執行緒區域物件。 例如：

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   **`sizeof`** 包含所要初始化物件的運算式並不會構成其本身的參考，並可在 c 和 c + + 中使用。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[執行緒區域儲存區（TLS）](../parallel/thread-local-storage-tls.md)
