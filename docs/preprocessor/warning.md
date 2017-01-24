---
title: "warning | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "warning_CPP"
  - "vc-pragma.warning"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "pop warning pragma"
  - "Pragma, warning"
  - "push pragma warning"
  - "warning pragma"
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# warning
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

啟用選擇性修改編譯器警告訊息的行為。  
  
## 語法  
  
```  
  
      #pragma warning(   
      warning-specifier  
       :   
      warning-number-list [; warning-specifier : warning-number-list...] )  
#pragma warning( push[ ,n ] )  
#pragma warning( pop )  
```  
  
## 備註  
 以下是可用的警告指定名稱參數。  
  
|警告指定名稱|意義|  
|------------|--------|  
|`1, 2, 3, 4`|將指定的層級套用至指定的警告。  這樣也會開啟預設為關閉的指定警告。|  
|`default`|將警告行為重設為預設值。  這樣也會開啟預設為關閉的指定警告。  警告會以其記載的預設層級產生。<br /><br /> 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../preprocessor/compiler-warnings-that-are-off-by-default.md)。|  
|`disable`|不發出指定的警告訊息。|  
|`error`|將指定的警告回報為錯誤。|  
|`once`|只顯示指定的訊息一次。|  
|`suppress`|將 pragma 的目前狀態推送到堆疊上，停用為下一行指定的警告，然後推出警告堆疊以重設 pragma 狀態。|  
  
 下列程式碼陳述式將說明 `warning-number-list` 參數可以包含多個警告編號，而且可以在相同的 pragma 指示詞中指定多個 `warning-specifier` 參數。  
  
```  
#pragma warning( disable : 4507 34; once : 4385; error : 164 )  
```  
  
 這項功能相當於下列程式碼。  
  
```  
// Disable warning messages 4507 and 4034.  
#pragma warning( disable : 4507 34 )  
  
// Issue warning 4385 only once.  
#pragma warning( once : 4385 )  
  
// Report warning 4164 as an error.  
#pragma warning( error : 164 )  
```  
  
 編譯器會將 0 和 999 之間的任何警告編號加上 4000。  
  
 對於在 4700\-4999 範圍內的警告編號 \(也就是與程式碼產生相關聯的編號\)，編譯器遇到函式的左大括號時生效的警告狀態，也會對函式的其餘部分生效。  若在函式中使用 `warning` pragma 變更編號大於 4699 之警告的狀態，該變更在函式結束之後才會生效。  下列範例將示範停用程式碼產生警告訊息，然後將它還原之 `warning` pragma 的正確位置。  
  
```  
// pragma_warning.cpp  
// compile with: /W1  
#pragma warning(disable:4700)  
void Test() {  
   int x;  
   int y = x;   // no C4700 here  
   #pragma warning(default:4700)   // C4700 enabled after Test ends  
}  
  
int main() {  
   int x;  
   int y = x;   // C4700  
}  
```  
  
 請注意，在整個函式主體中，`warning` pragma 的最後一項設定會對整個函式生效。  
  
## Push 和 Pop  
 `warning` pragma 也支援下列語法。  
  
 `#pragma warning(` `push` \[ `,``n` \] `)`  
  
 `#pragma warning(` `pop )`  
  
 其中 `n` 代表警告層級 \(1 至 4\)。  
  
 pragma `warning( push )` 會儲存每個警告的目前警告狀態。  pragma `warning( push,` `n``)` 會儲存每個警告的目前狀態，並且將全域警告層級設定為 `n`。  
  
 pragma `warning( pop )` 會將推送至堆疊的最後警告狀態推出。  您在 `push` 和 `pop` 之間對警告狀態所做的任何變更都會復原。  請考量以下範例：  
  
```  
#pragma warning( push )  
#pragma warning( disable : 4705 )  
#pragma warning( disable : 4706 )  
#pragma warning( disable : 4707 )  
// Some code  
#pragma warning( pop )   
```  
  
 在這個程式碼結束時，`pop` 會將每個警告的狀態 \(包括 4705、4706 和 4707\) 還原為程式碼開始時的狀態。  
  
 當您撰寫標頭檔時，可以使用 `push` 和 `pop` 確保使用者所做的警告狀態變更不會造成標頭無法正確編譯。  請在標頭的開頭使用 `push`，並且在結尾使用 `pop`。  例如，如果您的標頭未在警告層級 4 清楚編譯，則下列程式碼會將警告層級變更為 3，然後在標頭結尾還原為原始警告層級。  
  
```  
#pragma warning( push, 3 )  
// Declarations/definitions  
#pragma warning( pop )   
```  
  
 如需協助您隱藏警告之編譯器選項的詳細資訊，請參閱 [\/FI](../build/reference/fi-name-forced-include-file.md) 和 [\/w](../build/reference/compiler-option-warning-level.md)。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)