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
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371905"
---
# <a name="volatile-c"></a>volatile (C++)

類型限定詞，可以用來宣告程式中的物件可以由硬體修改。

## <a name="syntax"></a>語法

```
volatile declarator ;
```

## <a name="remarks"></a>備註

可以使用[/volatile](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器開關修改編譯器解釋此關鍵字的方式。

Visual Studio 根據目標體系結構的不同對**易失性**關鍵字的解釋不同。 對於 ARM,如果未指定 **/易失性**編譯器選項,編譯器將執行,就像指定**了 /volatile:iso 一**樣。 對於 ARM 以外的體系結構,如果未指定 **/易失性**編譯器選項,編譯器將執行,就像指定**了 /volatile:ms;** 因此,對於 ARM 以外的體系結構,我們強烈建議您指定 **/volatile:iso**,並在處理跨線程共用的記憶體時使用顯式同步基元和編譯器內部函數。

可以使用**易失性**限定符提供對非同步進程(如中斷處理程式)使用的記憶體位置的訪問。

當在也具有[__restrict](../cpp/extension-restrict.md)關鍵字的變數上使用**易失性**時,**易失性**優先。

如果**結構**成員標記為**易失性**,則**揮發性**將傳播到整個結構。 如果結構的長度不能使用一個指令在目前架構結構上複製,則該結構上可能會完全失去**易失性**。

如果以下條件之一為 true,**則 volatile**關鍵字可能對欄位沒有影響:

- volatile 欄位長度超過可透過單一指令複製到目前架構的大小上限。

- 最外層包含**結構**的長度(或者如果它是可能嵌套**結構**的成員)超過了使用一個指令可在當前體系結構上複製的最大大小。

儘管處理器不重新排序不可緩存的記憶體訪問,但不可緩存的變數必須標記為**易失性**,以確保編譯器不會重新排序記憶體訪問。

在某些優化中,聲明為**易失性**的物件不會使用,因為它們的值可以隨時更改。  即使先前指令要求相同物件的值，再次被要求時，系統一定會讀取暫時性物件目前的值。  此外，物件的值會在指派時立即被寫入。

## <a name="iso-compliant"></a>符合 ISO 標準

如果您熟悉 C# 易失性關鍵字,或者熟悉早期版本中的 Microsoft C++ 編譯器 (MSVC) 中的**易失性**行為,請注意,C++11 ISO 標準**易失性**關鍵字不同,在指定[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項時,MSVC 中支援該關鍵字。 (對於 ARM 系統來說，預設為指定)。 C++11 ISO 標準代碼中的**易失性**關鍵字僅用於硬體訪問;不要將其用於線程間通信。 對於線程間通信,請使用[C++標準庫中](../standard-library/cpp-standard-library-reference.md)的[\<std:atomic T>](../standard-library/atomic.md)等機制。

## <a name="end-of-iso-compliant"></a>符合 ISO 標準結尾

**Microsoft 特定的**

當使用 **/volatile:ms**編譯器選項時(預設情況下,當 ARM 以外的體系結構被定位時)編譯器生成額外的代碼,以保持對易失性物件的引用之間的排序,此外還保持對其他全域物件的引用的排序。 尤其是：

- 暫時性物件的寫入 (也稱為暫時性寫入) 有 Release 語義，也就是說，在指令序列中暫時性物件寫入之前的全域或靜態物件參考，會在已編譯二進位檔中的暫時性寫入之前發生。

- 暫時性物件的讀取 (也稱為暫時性讀取) 有 Acquire 語義，也就是說，在指令序列中揮發性記憶體讀取之後的全域或靜態物件參考，會在已編譯二進位檔中的暫時性讀取之後發生。

這可讓暫時性物件用於多執行緒應用程式的記憶體鎖定和記憶體釋放。

> [!NOTE]
> 當它依賴於使用 **/volatile:ms**編譯器選項時提供的增強保證時,代碼是不可移植的。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const 和易失性指標](../cpp/const-and-volatile-pointers.md)
