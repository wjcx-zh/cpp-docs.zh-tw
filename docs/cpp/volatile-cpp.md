---
title: "volatile （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- volatile_cpp
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
caps.latest.revision: 43
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1bbbceaa8f170ad8c75173d60d38e5dd3df1fbdd
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="volatile-c"></a>volatile (C++)
類型限定詞，可以用來宣告程式中的物件可以由硬體修改。  
  
## <a name="syntax"></a>語法  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>備註  
 您可以使用[/volatile](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器參數，修改編譯器如何解譯這個關鍵字。  
  
 Visual Studio 會根據目標架構，對`volatile` 關鍵字做不一樣的解譯。 若是 ARM、 如果有任何**/volatile**指定編譯器選項時，編譯器會執行如同**/volatile:iso**所指定。 針對 ARM，如果沒有以外的架構**/volatile**指定編譯器選項時，編譯器會執行如同**/volatile: ms**指定; 因此，對於架構以外 ARM 我們強烈建議您指定**/volatile:iso**，並在處理跨執行緒共用的記憶體時使用明確的同步處理原始類型和編譯器內建函式。  
  
 您可以使用 `volatile` 限定詞存取非同步處理序 (例如中斷處理常式) 所用的記憶體位置。  
  
 當`volatile`上也有變數使用[__restrict](../cpp/extension-restrict.md)關鍵字，`volatile`優先。  
  
 如果 `struct` 成員被標記為 `volatile`，則 `volatile` 會傳播至整個結構。 如果結構沒有足夠的長度，可透過單一指令複製到目前的架構，`volatile` 在該結構上可能會完全遺失。  
  
 如果下列其中一個條件成立，`volatile` 關鍵字可能對欄位無效：  
  
-   volatile 欄位長度超過可透過單一指令複製到目前架構的大小上限。  
  
-   最外層包含 `struct` 的長度，或者如果是可能巢狀 `struct` 的成員，超過可透過單一指令複製到目前架構的大小上限。  
  
 雖然處理器不會重新排列不可快取的記憶體存取，不可快取的變數必須標記成 `volatile` 以確保編譯器不會重新排列記憶體存取。  
  
 宣告成 `volatile` 的物件不用於某些最佳化，因為它們的值可能隨時會變更。  即使先前指令要求相同物件的值，再次被要求時，系統一定會讀取暫時性物件目前的值。  此外，物件的值會在指派時立即被寫入。  
  
## <a name="iso-compliant"></a>符合 ISO 標準  
 如果您是熟悉 C# volatile 關鍵字或熟悉的行為`volatile`在舊版的 Visual c + + 中，請注意，C + + 11 ISO 標準`volatile`關鍵字是不同，適用於 Visual Studio 時[//volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項已指定。 (對於 ARM 系統來說，預設為指定)。 `volatile` 關鍵字在 C++11 ISO 標準程式碼中只用於硬體存取；請勿將它用於執行緒間通訊。 用於執行緒間通訊使用機制如[std::atomic\<T >](../standard-library/atomic.md)從[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)。  
  
## <a name="end-of-iso-compliant"></a>符合 ISO 標準結尾  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
 時**/volatile: ms**編譯器選項使用 — ARM 以外的架構做為目標時，根據預設，編譯器會產生額外的程式碼維護除了維護暫時性物件參考的順序其他全域物件參考的順序。 特別之處在於：  
  
-   暫時性物件的寫入 (也稱為暫時性寫入) 有 Release 語義，也就是說，在指令序列中暫時性物件寫入之前的全域或靜態物件參考，會在已編譯二進位檔中的暫時性寫入之前發生。  
  
-   暫時性物件的讀取 (也稱為暫時性讀取) 有 Acquire 語義，也就是說，在指令序列中揮發性記憶體讀取之後的全域或靜態物件參考，會在已編譯二進位檔中的暫時性讀取之後發生。  
  
 這可讓暫時性物件用於多執行緒應用程式的記憶體鎖定和記憶體釋放。  
  
> [!NOTE]
>  當它是倚賴時具有所提供的增強型保證**/volatile: ms**編譯器選項時，程式碼是不可移植。  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)
