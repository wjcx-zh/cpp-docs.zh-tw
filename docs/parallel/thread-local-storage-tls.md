---
title: "執行緒區域儲存區 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "多執行緒 [C++], 執行緒區域儲存區"
  - "儲存執行緒特定的資料"
  - "thread 屬性"
  - "執行緒區域儲存區 [C++]"
  - "執行緒 [C++], 執行緒區域儲存區"
  - "TLS [C++]"
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 執行緒區域儲存區
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行緒區域儲存區 \(Thread Local Storage，TLS\) 是一種方法，讓指定之多執行緒處理序中的每個執行緒用來配置位置，以儲存執行緒特定資料。  動態繫結 \(執行階段\) 的執行緒特定資料是透過 TLS API 支援 \([TlsAlloc](assetId:///TlsAlloc?qualifyHint=False&autoUpgrade=True)、[TlsGetValue](assetId:///TlsGetValue?qualifyHint=False&autoUpgrade=True)、[TlsSetValue](assetId:///TlsSetValue?qualifyHint=False&autoUpgrade=True) 和 [TlsFree](assetId:///TlsFree?qualifyHint=False&autoUpgrade=True)\)。  如需有關如何在 Windows 上實作執行緒區域儲存區的詳細資訊，請參閱[執行緒區域儲存區 \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686749\(v=vs.85\).aspx)。  除了現有的 API 實作以外，Win32 和 Visual C\+\+ 編譯器現在支援靜態繫結 \(載入時間\) 的個別執行緒資料。  
  
##  <a name="_core_compiler_implementation_for_tls"></a> TLS 的編譯器實作  
 **C\+\+11：** `thread_local` 儲存類別規範是建議用來指定物件的執行緒區域儲存區和類別成員的方式。  如需詳細資訊，請參閱[儲存類別 \(C\+\+\)](../cpp/storage-classes-cpp.md#thread_local)。  
  
 Visual C\+\+ 也提供 Microsoft 特定屬性 \([執行緒](../cpp/thread.md)\) 做為延伸的儲存類別修飾詞。  使用 `__declspec` 關鍵字來宣告 **thread** 變數。  例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## 規則與限制  
 當您宣告靜態繫結的執行緒區域物件和變數時，必須遵守下列指導方針：  這些指導方針會套用至 [執行緒](../cpp/thread.md)，並於大多數的情況下也會套用至 [thread\_local](../cpp/storage-classes-cpp.md#thread_local)：  
  
-   `thread` 屬性只可以套用至類別和資料宣告和定義。  它不可使用於函式宣告或定義。  例如，下列程式碼會產生編譯器錯誤：  
  
    ```  
  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
-   只能在具有 `static` 範圍的資料項目上指定`thread` 修飾詞。  這包括 C\+\+ 類別的全域資料物件 \(`static` 和 `extern`\)、區域靜態物件和靜態資料成員。  無法使用 `thread` 屬性來宣告自動資料物件。  下列程式碼會產生編譯器錯誤：  
  
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
  
-   執行緒區域物件的宣告和定義都必須指定 `thread` 屬性。  例如，下列程式碼會產生錯誤：  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
-   `thread` 屬性不能做為類型修飾詞。  例如，下列程式碼會產生編譯器錯誤：  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
-   因為允許使用 `thread` 屬性進行 C\+\+ 物件的宣告，所以下列兩個範例在語意上是相同的：  
  
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
  
-   執行緒區域物件的位址不會被視為常數，而且任何包含這種位址的運算式都不會被視為常數運算式。  在標準 C 中，其效果是禁止使用執行緒區域變數的位址做為物件或指標的初始設定式。  例如，C 編譯器會將下列程式碼標示為錯誤：  
  
    ```  
  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     這項限制不適用於 C\+\+。  因為 C\+\+ 允許所有物件的動態初始化，所以您可使用採用執行緒區域變數位址的運算式來初始化物件。  其完成方式就如同建構執行緒區域物件一樣。  例如，如果稍早所示的程式碼編譯為 C\+\+ 原始程式檔，則不會產生錯誤。  請注意，只要採用執行緒區域變數位址的執行緒仍存在，此位址就有效。  
  
-   標準 C 允許利用需要自我參考的運算式來初始化物件或變數，但只限於非靜態範圍的物件。  雖然 C\+\+ 通常允利用需要自我參考的運算式來動態初始化對物件，但此種初始化不適用於執行緒區域物件。  例如:  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     請注意，包含所要初始化物件的 `sizeof` 運算式並不代表其本身的參考，但在 C 和 C\+\+ 中皆已啟用。  
  
     C\+\+ 不允許執行緒資料的這類動態初始化，因為執行緒區域儲存區設備未來可能會增強。  
  
-   在 [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] 之前的 Windows 作業系統上，`__declspec`\(thread\) 有一些限制。  如果 DLL 將任何資料或物件宣告為 `__declspec`\(thread\)，可能會造成保護錯誤 \(若以動態方式載入\)。  透過 [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175) 載入 DLL 之後，每當程式碼參考 `__declspec`\(thread\) 資料時，它會導致系統失敗。  因為執行緒的全域變數空間是在執行階段進行配置，所以此空間的大小是以應用程式的需求，再加上以靜態方式連結之所有 DLL 的需求的計算為基礎。  當您使用 `LoadLibrary` 時，您無法擴充此空間以便使用 `__declspec`\(thread\) 宣告執行緒區域變數。  如果您的 DLL 可透過 `LoadLibrary` 載入，則在 DLL 中使用 TLS API \(例如 [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801)\) 來配置 TLS。  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)   
 [TLS 的規則和限制](../misc/rules-and-limitations-for-tls.md)