---
title: "dllexport、dllimport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "dllimport_cpp"
  - "dllexport_cpp"
  - "dllexport"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], dllexport"
  - "__declspec 關鍵字 [C++], dllimport"
  - "dllexport __declspec 關鍵字"
  - "dllimport __declspec 關鍵字"
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# dllexport、dllimport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `dllexport` 和 **dllimport** 儲存類別屬性是 Microsoft 專有的 C 和 C\+\+ 語言擴充功能。  您可以使用它們在 DLL 中匯出和匯入函式、資料和物件。  
  
## 語法  
  
```  
  
        __declspec( dllimport ) declarator  
__declspec( dllexport ) declarator  
```  
  
## 備註  
 這些屬性明確定義其用戶端的 DLL 介面 \(可以是可執行檔或另一個 DLL\)。  將函式宣告為 `dllexport` 不需要模組定義 \(.def\) 檔，至少有關輸出的函式規格方面是如此。  `dllexport` 屬性會取代 `__export` 關鍵字。  
  
 如果類別已標記為 declspec\(dllexport\)，在類別階層中類別樣板的特製化會隱含標記為 declspec\(dllexport\)。  這表示類別樣板是明確具現化，必須定義類別的成員。  
  
 函式的 `dllexport` 會以其裝飾名稱公開函式。  對於 C\+\+ 函式，這包括名稱修飾 \(Name Mangling\)。  對於 C 函式或宣告為 `extern "C"` 的函式，其中包括根據呼叫慣例的平台專屬裝飾。  如需 C\/C\+\+ 程式碼中名稱裝飾的相關資訊，請參閱[裝飾名稱](../build/reference/decorated-names.md)。  使用 `__cdecl` 呼叫慣例，不會將名稱裝飾套用至已匯出的 C 函式或 C\+\+ `extern "C"` 函式。  
  
 若要匯出未裝飾的名稱，則連結方式是使用在 EXPORTS 區段中定義未裝飾名稱的模組定義 \(.def\) 檔。  如需詳細資訊，請參閱 [EXPORTS](../build/reference/exports.md)。  匯出未裝飾名稱的另一種方式是在原始程式碼中使用 `#pragma comment(linker, "/export:``alias``=``decorated_name``")` 指示詞。  
  
 當您宣告 `dllexport` 或 **dllimport** 時，您必須使用[擴充屬性語法](../cpp/declspec.md)和 `__declspec` 關鍵字。  
  
## 範例  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 或者，您可以使用巨集定義讓程式碼更容易讀取：  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 如需詳細資訊，請參閱:  
  
-   [定義和宣告](../cpp/definitions-and-declarations-cpp.md)  
  
-   [使用 dllexport 和 dllimport 定義內嵌 C\+\+ 函式](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [一般規則和限制](../cpp/general-rules-and-limitations.md)  
  
-   [在 C\+\+ 類別中使用 dllimport 和 dllexport](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)