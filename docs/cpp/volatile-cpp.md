---
title: volatile （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- volatile_cpp
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82ea6211a51bbe45fa1613dd7bb682f363783367
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461919"
---
# <a name="volatile-c"></a>volatile (C++)
類型限定詞，可以用來宣告程式中的物件可以由硬體修改。  
  
## <a name="syntax"></a>語法  
  
```  
volatile declarator ;  
```  
  
## <a name="remarks"></a>備註  
 您可以使用[/volatile](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器參數，修改編譯器如何解譯這個關鍵字。  
  
 Visual Studio 會解譯**volatile**以不同的方式根據目標架構的關鍵字。 為 ARM，如果沒有 **/volatile**指定編譯器選項時，編譯器會執行如同 **/volatile:iso**所指定。 適用於 ARM，如果沒有以外的架構 **/volatile**指定編譯器選項時，編譯器會執行如同 **/volatile: ms**指定; 因此，對於架構以外 ARM 我們強烈建議您指定 **/volatile:iso**，並使用明確的同步處理原始物件和編譯器內建函式，當您處理跨執行緒共用的記憶體。  
  
 您可以使用**volatile**限定詞存取非同步處理序，例如中斷處理常式所使用的記憶體位置。  
  
 時**volatile**的變數，也有適用於[__restrict](../cpp/extension-restrict.md)關鍵字**變動性**會優先使用。  
  
 如果**結構**成員會標示為**volatile**，然後**volatile**傳播至整個結構。 如果結構沒有長度，可複製目前架構上使用一個指令**volatile**可能會完全遺失該結構上。  
  
 **Volatile**關鍵字可能不會影響欄位，如果其中一個下列條件成立：  
  
-   volatile 欄位長度超過可透過單一指令複製到目前架構的大小上限。  
  
-   最外層包含長度**結構**— 或者它是可能巢狀的成員**結構**— 超過可透過單一指令複製到目前架構的大小上限。  
  
 雖然處理器不會不會重新排列不可快取的記憶體存取，必須標示為不可快取的變數**volatile**以確保編譯器不重新排列記憶體存取。  
  
 宣告為物件**volatile**不會用於某些最佳化功能因為隨時都可以變更其值。  即使先前指令要求相同物件的值，再次被要求時，系統一定會讀取暫時性物件目前的值。  此外，物件的值會在指派時立即被寫入。  
  
## <a name="iso-compliant"></a>符合 ISO 標準  
 如果您是熟悉 C# volatile 關鍵字，或熟悉的行為**volatile**在舊版的 Visual c + + 中，請注意，c++11 ISO Standard **volatile**關鍵字是不同，Visual Studio 支援時[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)指定編譯器選項。 (對於 ARM 系統來說，預設為指定)。 **Volatile**關鍵字在 C + + 11 ISO 標準的程式碼是只用於硬體存取; 請勿使用它對於執行緒間通訊。 對於執行緒間通訊使用機制如[std:: atomic\<T >](../standard-library/atomic.md)從[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)。  
  
## <a name="end-of-iso-compliant"></a>符合 ISO 標準結尾  
  
## <a name="microsoft-specific"></a>Microsoft 特定的  
 當 **/volatile: ms**使用編譯器選項 — ARM 以外的架構為目標時，預設情況 — 編譯器會產生額外的程式碼來維護對 volatile 物件除了維護參考的順序其他全域物件參考的順序。 特別之處在於：  
  
-   暫時性物件的寫入 (也稱為暫時性寫入) 有 Release 語義，也就是說，在指令序列中暫時性物件寫入之前的全域或靜態物件參考，會在已編譯二進位檔中的暫時性寫入之前發生。  
  
-   暫時性物件的讀取 (也稱為暫時性讀取) 有 Acquire 語義，也就是說，在指令序列中揮發性記憶體讀取之後的全域或靜態物件參考，會在已編譯二進位檔中的暫時性讀取之後發生。  
  
 這可讓暫時性物件用於多執行緒應用程式的記憶體鎖定和記憶體釋放。  
  
> [!NOTE]
>  當它需倚賴時具有所提供的增強型保證 **/volatile: ms**編譯器選項時，程式碼是不可移植。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)