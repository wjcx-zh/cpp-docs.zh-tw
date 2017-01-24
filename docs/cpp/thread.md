---
title: "執行緒 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "thread"
  - "thread_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], 執行緒"
  - "thread __declspec 關鍵字"
  - "執行緒區域儲存區 (TLS)"
  - "TLS (執行緒區域儲存區), 編譯器實作"
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 執行緒
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 **thread** 擴充儲存類別修飾詞是用來宣告執行緒區域變數。  對於 C\+\+11 中的可攜式對等項目，使用 [thread\_local](../cpp/storage-classes-cpp.md#thread_local) 儲存類別規範。  
  
## 語法  
  
```  
  
__declspec( thread ) declarator  
```  
  
## 備註  
 執行緒區域儲存區 \(Thread Local Storage，TLS\) 是一種機制，讓多執行緒處理序中的每個執行緒用來配置儲存區，以儲存執行緒特定資料。  在標準多執行緒程式中，資料是在特定處理序的所有執行緒之間共用，而執行緒區域儲存區則是用於配置每個執行緒資料的機制。  如需執行緒的完整討論，請參閱[多執行緒](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 執行緒區域變數的宣告必須使用[擴充屬性語法](../cpp/declspec.md)和 `__declspec` 關鍵字與 **thread** 關鍵字。  例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 在宣告執行緒區域物件和變數時，您必須遵守下列方針：  
  
-   您只能將 **thread** 屬性套用至類別以及資料宣告和定義；**thread** 不能用於函式宣告或定義。  
  
-   使用 **thread** 屬性可能會干擾 DLL 匯入的[延遲載入](../build/reference/linker-support-for-delay-loaded-dlls.md)**。**  
  
-   在 XP 系統上，如果 DLL 使用 \_\_declspec\(thread\) 資料並透過 LoadLibrary 予以動態載入，則 `thread` 可能無法正確運作。  
  
-   您只能在具有靜態儲存期的資料項目上指定 **thread** 屬性。  這包括全域資料物件 \(**static** 和 `extern`\)、區域靜態物件和類別的靜態資料成員。  您無法使用 **thread** 屬性來宣告自動資料物件。  
  
-   不論是在相同的檔案還是不同的檔案進行宣告和定義，您都必須將 **thread** 屬性用於執行緒區域物件的宣告和定義中。  
  
-   您不能使用 **thread** 屬性做為類型修飾詞。  
  
-   因為允許使用 **thread** 屬性進行物件的宣告，下列兩個範例在語意上是相同的：  
  
    ```  
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
  
-   標準的 C 允許使用需要自我參考的運算式來初始化物件或變數，但只限於非靜態範圍的物件。  雖然 C\+\+ 通常允許使用需要自我參考的運算式來對物件進行動態初始化，但這種類型的初始化不適用於執行緒區域物件。  例如:  
  
    ```  
    // declspec_thread_3.cpp  
    // compile with: /LD  
    #define Thread __declspec( thread )  
    int j = j;   // Okay in C++; C error  
    Thread int tls_i = sizeof( tls_i );   // Okay in C and C++  
    ```  
  
     請注意，包含所要初始化物件的 `sizeof` 運算式並不會構成其本身的參考，但在 C 和 C\+\+ 中都是允許的。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [執行緒區域儲存區](../parallel/thread-local-storage-tls.md)