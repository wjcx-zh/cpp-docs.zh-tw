---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: bbdd7d03d820b9fc0d541dbb31d55b641226f14e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213095"
---
# <a name="volatile-c"></a>volatile (C++)

類型限定詞，可以用來宣告程式中的物件可以由硬體修改。

## <a name="syntax"></a>語法

```
volatile declarator ;
```

## <a name="remarks"></a>備註

您可以使用[/volatile](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器參數來修改編譯器如何解讀此關鍵字。

Visual Studio 會根據 **`volatile`** 目標架構，以不同的方式來解讀關鍵字。 針對 ARM，如果未指定 **/volatile**編譯器選項，則編譯器會執行，如同已指定 **/volatile： iso** 。 針對 ARM 以外的架構，如果未指定 **/volatile**編譯器選項，編譯器會執行，如同已指定 **/volatile： ms**一樣。因此，對於 ARM 以外的架構，我們強烈建議您指定 **/volatile： iso**，並在處理跨執行緒共用的記憶體時，使用明確的同步處理原始物件和編譯器內建函式。

您可以使用 **`volatile`** 限定詞來提供非同步處理常式所使用之記憶體位置的存取權，例如中斷處理常式。

當 **`volatile`** 用於也具有[__restrict](../cpp/extension-restrict.md)關鍵字的變數時， **`volatile`** 會優先使用。

如果 **`struct`** 成員已標記為 **`volatile`** ，則 **`volatile`** 會傳播到整個結構。 如果結構沒有可使用一個指令複製到目前架構上的長度， **`volatile`** 可能會在該結構上完全遺失。

**`volatile`** 如果下列其中一個條件成立，關鍵字可能不會影響欄位：

- volatile 欄位長度超過可透過單一指令複製到目前架構的大小上限。

- 最外層包含的長度 **`struct`** （如果它是可能嵌套的成員 **`struct`** ）超過可使用一個指令複製到目前架構上的大小上限。

雖然處理器不會重新排列無法快取的記憶體存取，但是無法快取的變數必須標示為， **`volatile`** 以確保編譯器不會重新排序記憶體存取。

宣告為的物件 **`volatile`** 不會在特定優化中使用，因為它們的值可以隨時變更。  即使先前指令要求相同物件的值，再次被要求時，系統一定會讀取暫時性物件目前的值。  此外，物件的值會在指派時立即被寫入。

## <a name="iso-compliant"></a>符合 ISO 標準

如果您熟悉 c # volatile 關鍵字，或熟悉 **`volatile`** 舊版 Microsoft c + + 編譯器（MSVC）中的行為，請注意 c + + 11 ISO Standard **`volatile`** 關鍵字是不同的，而且當指定[/volatile： ISO](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項時，會在 MSVC 中受到支援。 (對於 ARM 系統來說，預設為指定)。 **`volatile`** C + + 11 ISO 標準程式碼中的關鍵字僅用於硬體存取; 請勿將它用於執行緒間的通訊。 對於執行緒間通訊，請使用[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)中的機制（例如[std：： \<T> ](../standard-library/atomic.md)不可部分完成）。

## <a name="end-of-iso-compliant"></a>符合 ISO 標準結尾

**Microsoft 特定的**

使用 **/volatile： ms**編譯器選項時—根據預設，當 ARM 以外的架構為目標時，編譯器會產生額外的程式碼來維護對 volatile 物件之參考的順序，以及維護其他全域物件參考的順序。 尤其是：

- 暫時性物件的寫入 (也稱為暫時性寫入) 有 Release 語義，也就是說，在指令序列中暫時性物件寫入之前的全域或靜態物件參考，會在已編譯二進位檔中的暫時性寫入之前發生。

- 暫時性物件的讀取 (也稱為暫時性讀取) 有 Acquire 語義，也就是說，在指令序列中揮發性記憶體讀取之後的全域或靜態物件參考，會在已編譯二進位檔中的暫時性讀取之後發生。

這可讓暫時性物件用於多執行緒應用程式的記憶體鎖定和記憶體釋放。

> [!NOTE]
> 當使用 **/volatile： ms**編譯器選項時所提供的增強保證時，程式碼是不可移植的。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const 和 volatile 指標](../cpp/const-and-volatile-pointers.md)
