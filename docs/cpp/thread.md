---
title: thread
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 59a1af8a7eb73207f84ddf2194d5fe9e77d7d46a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221970"
---
# <a name="thread"></a>thread

**Microsoft 專屬**

**執行緒**擴充的儲存類別修飾詞用來宣告執行緒區域變數。 針對可攜式 C + + 11 中的對等及更新版本中，使用[thread_local](../cpp/storage-classes-cpp.md#thread_local)可攜式程式碼的儲存類別規範。 在 Windows 上`thread_local`透過實作 **__declspec （thread)**。

## <a name="syntax"></a>語法

> **__declspec( thread )** *declarator*

## <a name="remarks"></a>備註

執行緒區域儲存區 (Thread Local Storage，TLS) 是一種機制，讓多執行緒處理序中的每個執行緒用來配置儲存區，以儲存執行緒特定資料。 在標準多執行緒程式中，資料是在特定處理序的所有執行緒之間共用，而執行緒區域儲存區則是用於配置每個執行緒資料的機制。 如需執行緒的完整討論，請參閱 <<c0> [ 進行多執行緒處理](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

必須使用執行緒區域變數的宣告[擴充屬性語法](../cpp/declspec.md)並 **__declspec**關鍵字搭配**執行緒**關鍵字。 例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```cpp
__declspec( thread ) int tls_i = 1;
```

使用執行緒區域變數中時以動態方式載入的程式庫，您需要留意可能會導致不正確地初始化的執行緒本機變數的因素：

1. 如果變數初始化函式呼叫 （包括建構函式），將只能之執行緒的此二進位檔/dll 載入程序，以及已載入的二進位檔/DLL 之後，啟動這些執行緒中呼叫此函式。 初始化函式不會載入 DLL 時已執行的任何其他執行緒呼叫。 動態初始化，就會發生 DLL_THREAD_ATTACH，DllMain 呼叫但 DLL 永遠不會取得該訊息，如果 DLL 不是程序中，在執行緒啟動時。

1. 常數的值會以靜態方式初始化的執行緒本機變數通常會在所有執行緒上正確初始化。 不過，自 2017 年 12 月起沒有已知的一致性問題的 microsoftC++讓接收動態而不是靜態初始設定 constexpr 變數的編譯器。

   注意:這兩種問題有修正在未來的編譯器的更新。

此外，您必須在宣告執行緒區域物件和變數時，遵守這些指導方針：

- 您可以套用**執行緒**屬性至類別和資料宣告和定義;**執行緒**不能在函式宣告或定義。

- 您可以指定**執行緒**只能在具有靜態儲存期的資料項目上的屬性。 這包括全域資料物件 (兩者**靜態**並**extern**)、 區域靜態物件和類別的靜態資料成員。 您無法宣告自動資料物件**執行緒**屬性。

- 您必須使用**執行緒**屬性宣告和執行緒區域物件的定義，是否會發生在相同的檔案還是不同的檔案中的宣告和定義。

- 您無法使用**執行緒**做為類型修飾詞的屬性。

- 因為使用物件的宣告**執行緒**允許屬性、 這兩個範例在語意上與：

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

- 標準的 C 允許使用需要自我參考的運算式來初始化物件或變數，但只限於非靜態範圍的物件。 雖然 C++ 通常允許使用需要自我參考的運算式來對物件進行動態初始化，但這種類型的初始化不適用於執行緒區域物件。 例如：

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   請注意， **sizeof**運算式，其中包含要初始化的物件不會構成本身的參考，且能在 C 和C++。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[執行緒區域儲存區 (TLS)](../parallel/thread-local-storage-tls.md)