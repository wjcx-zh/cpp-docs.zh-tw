---
title: "執行緒 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: thread_cpp
dev_langs: C++
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b26487e7f5f11bb32f418b438e9d0396b5854a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="thread"></a>thread

**Microsoft 特定的**  
**執行緒**擴充的儲存類別修飾詞用來宣告執行緒區域變數。 用於可攜式相當於 C + + 11 和更新版本、 [thread_local](../cpp/storage-classes-cpp.md#thread_local)可攜式程式碼的儲存類別規範。 在 Windows 上**thread_local**實作與**__declspec （thread)**。

## <a name="syntax"></a>語法

```
__declspec( thread ) declarator
```

## <a name="remarks"></a>備註

執行緒區域儲存區 (Thread Local Storage，TLS) 是一種機制，讓多執行緒處理序中的每個執行緒用來配置儲存區，以儲存執行緒特定資料。 在標準多執行緒程式中，資料是在特定處理序的所有執行緒之間共用，而執行緒區域儲存區則是用於配置每個執行緒資料的機制。 如需執行緒的完整討論，請參閱[多執行緒](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

執行緒區域變數的宣告都必須使用[擴充屬性語法](../cpp/declspec.md)和`__declspec`關鍵字搭配**執行緒**關鍵字。 例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：

```cpp
__declspec( thread ) int tls_i = 1;  
```

使用執行緒區域變數中時以動態方式載入程式庫，您需要留意的因素可能會導致不正確地初始化執行緒區域變數：

1) 如果變數初始化函式呼叫 （包括建構函式），執行緒造成二進位/DLL 載入程序，以及載入二進位檔/DLL 之後，啟動這些執行緒只會呼叫此函式。 初始化函式不會針對已經在已載入 DLL 時執行的其他任何執行緒呼叫。 動態初始化，就會發生 DLL_THREAD_ATTACH，DllMain 呼叫而 DLL 永遠不會取得，如果在執行緒啟動時 DLL 不是程序中的訊息。 

2) 執行緒區域變數初始化靜態的常數值通常會在所有執行緒上正確初始化。 不過，自 2017 年 12 月沒有已知的一致性問題讓接收 constexpr 變數時，Microsoft c + + 編譯器中動態而不是靜態初始設定。  
  
   注意： 這兩種問題應該會固定在未來的編譯器的更新。


此外，您必須在宣告執行緒區域物件和變數時，遵守下列方針：

- 您可以套用**執行緒**屬性只能加入類別以及資料宣告和定義;**執行緒**不能在函式宣告或定義。

- 您可以指定**執行緒**只能在具有靜態儲存期的資料項目上的屬性。 這包括全域資料物件 (同時**靜態**和**extern**)、 區域靜態物件和類別的靜態資料成員。 您無法宣告自動資料物件與**執行緒**屬性。

- 您必須使用**執行緒**不論是在相同的檔案還是不同的檔案進行的宣告和定義的宣告和定義執行緒區域物件的屬性。

- 您無法使用**執行緒**屬性做為類型修飾詞。

- 由於物件宣告使用**執行緒**允許屬性、 這兩個範例語意相等：

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

- 標準的 C 允許使用需要自我參考的運算式來初始化物件或變數，但只限於非靜態範圍的物件。 雖然 C++ 通常允許使用需要自我參考的運算式來對物件進行動態初始化，但這種類型的初始化不適用於執行緒區域物件。 例如: 

    ```cpp
    // declspec_thread_3.cpp
    // compile with: /LD
    #define Thread __declspec( thread )
    int j = j;   // Okay in C++; C error
    Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
    ```

     請注意， **sizeof**運算式，其中包含所要初始化的物件不會構成其本身的參考，並允許在 C 和 c + + 中。

**結束 Microsoft 特定的**

## <a name="see-also"></a>請參閱

[__declspec](../cpp/declspec.md)  
[關鍵字](../cpp/keywords-cpp.md)  
[執行緒區域儲存區 (TLS)](../parallel/thread-local-storage-tls.md)
