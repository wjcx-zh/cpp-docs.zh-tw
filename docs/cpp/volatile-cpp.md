---
title: "volatile (C++) | Microsoft Docs"
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
  - "volatile_cpp"
  - "volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "中斷處理常式和 volatile 關鍵字"
  - "物件 [C++], volatile"
  - "volatile 關鍵字 [C++]"
  - "volatile 物件"
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
caps.latest.revision: 43
caps.handback.revision: 43
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# volatile (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以用來宣告一個物件可以在程式被硬體修改的一個型別限定詞。  
  
## 語法  
  
```  
  
volatile declarator ;  
```  
  
## 備註  
 您可以使用 [\/暫時的](../build/reference/volatile-volatile-keyword-interpretation.md) 編譯器切換並修改它如何詮釋這些關鍵字。  
  
 Visual Studio 會根據目標架構，對同一個`volatile` 關鍵字做不一樣的解釋。  對於 ARM 系統來說，如果 **\/volatile** 編譯器選項都沒有指定，編譯器就會以預設執行 **\/volatile:iso** 。  對於除了 ARM 以外的內部結構，如果 **\/volatile** 編譯器選項都沒有指定，編譯器會執行 **\/volatile:ms** ; 因此當您處理跨執行緒的共用記憶體時，我們強烈建議您指定 **\/volatile:iso**，並使用明確的同步處理原始物件和內建編譯器。  
  
 您可以使用 `volatile` 限定詞存取非同步處理序的記憶體位置，例如中斷處理常式。  
  
 當 `volatile` 被含有 [\_\_限制](../cpp/extension-restrict.md) 關鍵字的變數使用時， `volatile` 會取得優先權。  
  
 如果 `struct` 的成員被標記為 `volatile`，則 `volatile` 會傳遞至整個結構。  如果結構用單一指令卻沒有足夠的長度可以複製目前的結構， `volatile` 在該結構可能會遺失。  
  
 如果符合下列任一狀況， `volatile` 關鍵字可能會對欄位無效:  
  
-   暫時的欄位長度超過對大值，此最大值為用一個指令可以複製的目前結構。  
  
-   最外層包含 `struct`的長度，或者是可以有巢狀 `struct` 的成員—超過可以只用一個指令就能被複製在目前結構的最大值。  
  
 雖然這個處理器不重新排列非快取記憶體存取，非快取變數必須被標記成 `volatile` 確保編譯器不重新排列記憶體存取。  
  
 被宣告成 `volatile` 的物件不適用於某些最佳化，因為它們的值會隨時變更。即使先前指示要求相同物件的值，系統一定會讀取暫時物件目前的值。此外，物件的值會在工作中立即被寫入。  
  
## ISO\-Compliant \- ISO 相容  
 如果您熟悉 [C\# volatile](../Topic/volatile%20\(C%23%20Reference\).md) 關鍵字或在舊版的 Visual C\+\+熟悉 `volatile` 的行為，請注意 C\+\+11 ISO 標準 `volatile` 關鍵字是不同的且當 [\/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) 編譯器選項被指定時，亦支援 Visual Studio。\(對於 ARM 系統來說，它的指定為預設的\)。  `volatile` 關鍵字在 C\+\+11 ISO 標準程式碼中是只針對硬體存取;不要使用它來做內部執行緒的溝通。  如需內部執行緒溝通，請使用機制像是 [C\+\+ 標準樣板程式庫的](../standard-library/cpp-standard-library-reference.md) [std::atomic\<T\>](../standard-library/atomic.md) 。  
  
## ISO 標準的結尾  
  
## Microsoft 專有的  
 當 **\/volatile:ms** 編譯器選項預設是由 ARM以外的結構使用時，編譯器產生額外的程式碼維持參考對暫時物件的順序也維持參考對其他全域物件的順序。  特別之處在於：  
  
-   暫時物件 \(也稱為 Volatile 寫入\) 的寫入在語義上為釋放;即為對全域或靜態物件的參考在寫入至靜態物件之前的指令序列會發生在暫時寫入到二進位編譯之前。  
  
-   暫時物件 \(也稱為讀取 Volatile\) 的讀取在語義上為取得;即為對全域或靜態物件的參考在讀取揮發性記憶體至靜態物件之前的指令序列會發生在暫時讀取到二進位編譯之後。  
  
 這可讓暫時物件在多執行緒應用程式為記憶體鎖定和記憶體釋放的使用。  
  
> [!NOTE]
>  當它依靠 **\/volatile:ms** 編譯器選項被使用且更多確保時 ，程式碼就不可移植了。  
  
## 結束 Microsoft 專有  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)