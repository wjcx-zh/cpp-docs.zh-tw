---
title: "static_assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "C2338"
  - "static_assert_cpp"
  - "static_assert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "判斷提示 [C++], static_assert"
  - "C++ 關鍵字, static_assert"
  - "C2338"
  - "static_assert"
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# static_assert
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在編譯時期測試軟體判斷提示。  如果指定的常數運算式是 `false`，則編譯器會顯示指定的訊息，且編輯會失敗並產生錯誤 C2338，否則宣告沒有任何作用。  
  
## 語法  
  
```  
static_assert(   
    constant-expression,   
    string-literal   
);  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`constant-expression`|可以轉換為布林值的整數常數運算式。<br /><br /> 如果求出的運算式的值為零 \(false\)，則會顯示 `string-literal` 參數，且編譯會失敗並產生錯誤。  如果運算式為非零 \(true\)，則 `static_assert` 宣告沒有任何作用。|  
|`string-literal`|`constant-expression` 參數為零時顯示的訊息。  此訊息是編譯器的[基本字元集](../c-language/ascii-character-set.md)中的字元字串，也就是說，並不是[多位元組或寬字元](../c-language/multibyte-and-wide-characters.md)。|  
  
## 備註  
 `static_assert` 宣告的 `constant-expression` 參數代表「*軟體判斷提示*」\(Software Assertion\)。  軟體判斷提示會指定您希望在程式中的某個特定點為 true 的條件。  如果條件為 true，則 `static_assert` 宣告沒有任何作用。  如果條件為 false，則判斷提示會失敗，編譯器會在 `string-literal` 參數中顯示訊息，且編譯會失敗並產生錯誤。  
  
 `static_assert` 宣告會在編譯時期測試軟體判斷提示。  相反地，[assert 巨集、\_assert、\_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 巨集會在執行階段測試軟體判斷提示，因而佔用執行階段的空間或時間。  對樣板進行偵錯時，`static_assert` 宣告會特別實用，因為樣板引數可以包含在 `constant-expression` 參數中。  
  
 編譯器遇到 `static_assert` 宣告時，會檢查宣告中是否有語法錯誤。  如果 `constant-expression` 參數未相依於樣板參數，則編譯器會立即求值。  否則，編譯器會在樣板具現化時求出 `constant-expression` 參數值。  因此，編譯器可能會在遇到宣告時發出診斷資訊一次，並且在樣板具現化時再次發出訊息。  
  
 您可以在命名空間、類別或區塊範圍內使用 `static_assert` 關鍵字。\(由於 `static_assert` 關鍵字可以在命名空間範圍內使用，因此即使它不會在程式中引入新名稱，就技術上來說仍是一種宣告\)。  
  
## 說明  
 在下列範例中，`static_assert` 宣告具有命名空間範圍。  由於編譯器已知 `void *` 類型的大小，因此會立即計算運算式的值。  
  
## 範例  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## 說明  
 在下列範例中，`static_assert` 宣告具有類別範圍。  `static_assert` 會驗證樣板參數為「*一般舊資料*」\(Plain Old Data，POD\) 類型。  編譯器會在宣告 `static_assert` 時檢查此宣告，但是在 `main()` 中具現化 `basic_string` 類別樣板之前不會求出 `constant-expression` 參數值。  
  
## 範例  
  
```  
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(tr1::is_pod<CharT>::value,  
                  "Template argument CharT must be a POD type in class template basic_string");  
    // ...  
    };  
}  
struct NonPOD {  
    NonPOD(const NonPOD &) {}  
    virtual ~NonPOD() {}  
};  
int main()  
{  
    std::basic_string<char> bs;  
}  
```  
  
## 說明  
 在下列範例中，`static_assert` 宣告具有區塊範圍。  `static_assert` 會驗證 VMPage 結構的大小是否與系統的虛擬記憶體 pagesize 相等。  
  
## 範例  
  
```  
#include <sys/param.h> // defines PAGESIZE  
class VMMClient {  
public:  
    struct VMPage { // ...   
           };  
    int check_pagesize() {  
    static_assert(sizeof(VMPage) == PAGESIZE,  
        "Struct VMPage must be the same size as a system virtual memory page.");  
    // ...  
    }  
// ...  
};  
```  
  
## 請參閱  
 [判斷提示和使用者提供的訊息 \(C\+\+\)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [\#error 指示詞](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert 巨集、\_assert、\_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [樣板](../cpp/templates-cpp.md)   
 [ASCII 字元集](../c-language/ascii-character-set.md)   
 [宣告](../misc/declarations.md)