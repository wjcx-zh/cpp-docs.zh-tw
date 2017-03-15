---
title: "safebuffers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "safebuffers"
  - "safebuffers_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 (C++), safebuffers"
  - "safebuffers __declspec 關鍵字"
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# safebuffers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 告知編譯器不要插入函式的緩衝區滿溢安全性檢查。  
  
## 語法  
  
```  
__declspec( safebuffers )  
```  
  
## 備註  
 **\/GS** 編譯器選項會讓編譯器在堆疊上插入安全性檢查來測試緩衝區滿溢。  [\/GS \(緩衝區安全性檢查\)](../build/reference/gs-buffer-security-check.md) 中說明了適合進行安全性檢查的資料結構類型。  如需緩衝區滿溢偵測的詳細資訊，請參閱 MSDN 網站上的[深入了解編譯器安全性檢查](http://go.microsoft.com/fwlink/?linkid=7260)。  
  
 某位專業人員手動檢閱程式碼或進行外部分析後，可能會判斷函式不會發生緩衝區滿溢。  在這種情況下，您可以對函式宣告套用 \_\_`declspec(safebuffers)` 關鍵字來抑制函式的安全性檢查。  
  
> [!CAUTION]
>  緩衝區安全性檢查提供了重要的安全性保護，且幾乎不會對效能造成影響。  因此，除了在少數函式的效能為重要考量，以及函式已知為安全的情況以外，建議您不要抑制這些檢查。  
  
## 內嵌函式  
 一個「*主要函式*」\(Primary function\) 可以使用[內嵌](../misc/inline-inline-forceinline.md)關鍵字來插入「*次要函式*」\(Secondary function\) 的複本。  如果將 \_\_`declspec(safebuffers)` 關鍵字套用至函式，就會抑製該函式的緩衝區滿溢偵測。  不過，在下列方式中，內嵌會影響 \_\_`declspec(safebuffers)` 關鍵字。  
  
 假設已為兩個函式指定 **\/GS** 編譯器選項，但是主要功能指定了 \_\_`declspec(safebuffers)` 關鍵字。  第二個函式中的資料結構會使其進行安全性檢查，因此函式不會抑制這些檢查。  在此情況下：  
  
-   不論使用的是哪種編譯器最佳化，都可在次要函式上指定 [\_\_forceinline](../misc/inline-inline-forceinline.md) 關鍵字，以強制編譯器內嵌該函式。  
  
-   由於次要函式會進行安全性檢查，因此也會對主要函式套用安全性檢查，即使已對主要函式指定 \_\_`declspec(safebuffers)` 關鍵字。  
  
## 範例  
 下列程式碼將示範如何使用 \_\_`declspec(safebuffers)` 關鍵字。  
  
```  
// compile with: /c /GS  
typedef struct {  
    int x[20];  
} BUFFER;  
static int checkBuffers() {  
    BUFFER cb;  
    // Use the buffer...  
    return 0;  
};  
static __declspec(safebuffers)   
    int noCheckBuffers() {  
    BUFFER ncb;  
    // Use the buffer...  
    return 0;  
}  
int wmain() {  
    checkBuffers();  
    noCheckBuffers();  
    return 0;  
}  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [inline、\_\_inline、\_\_forceinline](../misc/inline-inline-forceinline.md)   
 [strict\_gs\_check](../preprocessor/strict-gs-check.md)