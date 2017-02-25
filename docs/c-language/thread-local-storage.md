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
  - "儲存體, 執行緒區域儲存區"
  - "執行緒儲存類別屬性"
  - "執行緒區域儲存區"
  - "執行緒區域變數"
  - "TLS (執行緒區域儲存區)"
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 執行緒區域儲存區
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 執行緒區域儲存區 \(Thread Local Storage，TLS\) 是一種機制，讓指定之多執行緒處理序中的每個執行緒用來配置儲存區，以儲存執行緒特定資料。  在標準多執行緒程式中，資料是在特定處理序的所有執行緒之間共用，而執行緒區域儲存區則是用於配置每個執行緒資料的機制。  如需執行緒的完整討論，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [中的 處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms684841)。  
  
 Microsoft C 語言包括擴充儲存類別屬性 thread，可搭配 \_\_declspec 關鍵字宣告執行緒區域變數。  例如，下列程式碼宣告整數執行緒區域變數，並使用值將它初始化：  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 當您宣告靜態繫結的執行緒區域變數時，必須遵守下列方針：  
  
-   使用 **\_\_declspec\(thread\)** 可能會干擾 DLL 匯入的[延遲載入](../build/reference/linker-support-for-delay-loaded-dlls.md)**。**  
  
-   您只能將 thread 屬性套用至資料宣告和定義。  它不可使用於函式宣告或定義。  例如，下列程式碼會產生編譯器錯誤：  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread void func();      /* Error */  
    ```  
  
-   您只能在具有靜態儲存期的資料項目上指定 thread 屬性。  這包括全域資料 \(同時包含 static 和 extern\) 和區域靜態資料。  您無法使用 thread 屬性宣告自動資料。  例如，下列程式碼會產生編譯器錯誤：  
  
    ```  
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
  
-   不論宣告和定義是發生在相同的檔案還是不同的檔案中，您都必須使用 thread 屬性宣告和定義執行緒區域資料。  例如，下列程式碼會產生錯誤：  
  
    ```  
    #define Thread   __declspec( thread )  
    extern int tls_i;     /* This generates an error, because the   */  
    int Thread tls_i;     /* declaration and the definition differ. */  
    ```  
  
-   您不能使用 thread 屬性做為類型修飾詞。  例如，下列程式碼會產生編譯器錯誤：  
  
    ```  
    char *ch __declspec( thread );      /* Error */  
    ```  
  
-   執行緒區域變數的位址不會被視為常數，而且任何包含這種位址的運算式都不會被視為常數運算式。  這表示，您不可使用執行緒區域變數的位址做為指標的初始設定式。  例如，編譯器會將下列程式碼標示為錯誤：  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i;  
    int *p = &tls_i;      /* Error */  
    ```  
  
-   C 允許使用需要自我參考的運算式來初始化變數，但只限於非靜態範圍的物件。  例如:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i = tls_i;             /* Error */  
    int j = j;                            /* Error */  
    Thread int tls_i = sizeof( tls_i )    /* Okay  */  
    ```  
  
     請注意，包含要初始化之變數的 sizeof 運算式並不會構成其本身的參考，因此可以使用。  
  
-   使用 **\_\_declspec\(thread\)** 可能會干擾 DLL 匯入的[延遲載入](../build/reference/linker-support-for-delay-loaded-dlls.md)**。**  
  
 如需使用 thread 屬性的詳細資訊，請參閱[多執行緒主題](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)