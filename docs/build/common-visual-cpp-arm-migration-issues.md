---
title: "Visual c + + ARM 移轉常見問題 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcc34d472fb6db02eb902001ad5aac77dea5baf0
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="common-visual-c-arm-migration-issues"></a>Visual C++ ARM 移轉時常見的問題

時使用 Microsoft Visual c + + (MSVC)，相同的 c + + 原始程式碼 x86 或 x64 架構上可能會產生不同的結果，在 ARM 架構上。

## <a name="sources-of-migration-issues"></a>移轉問題的來源

您將程式碼從 x86 或 x64 架構移轉至 ARM 架構時，可能會遇到的許多問題與相關原始碼建構，可能會叫用未定義，實作定義，或未指定的行為。

*未定義的行為*行為未定義的 c + + 標準，且有任何合理的結果所造成： 例如，將浮點值轉換成帶正負號的整數，或移位值的位置數目是負值或超過其升級後的類型中的位元的數字。

*實作定義的行為*是 c + + 標準需要編譯器廠商，以定義和文件的行為。 程式可以安全地依賴實作定義的行為，即使這樣做，可能無法移植。 定義實作之行為的範例包括內建資料類型和其對齊需求的大小。 實作定義的行為可能會影響作業的範例來存取變數引數清單。

*未指定行為*是 c + + 標準離開刻意不具決定性的行為。 行為會被視為不具決定性的雖然編譯器實作取決於特定的引動過程的未指定的行為。 不過，編譯器廠商預先決定的結果，或確保一致的行為，可比較的引動過程，之間不需要而且不需要的文件。 未指定的行為的範例為包含函式呼叫的引數中的子運算式的評估的順序。

其他的移轉問題可以將歸類為 ARM 和 x86 或 x64 架構，以不同的方式與 c + + 標準互動的硬體差異。 例如，x86 和 x64 架構的強式記憶體模型有`volatile`-限定變數以便特定種類的執行緒間通訊，在過去曾使用的一些額外的屬性。 但是 ARM 架構的弱式記憶體模型不支援這種使用，也無法 c + + 標準不需要它。

> [!IMPORTANT]
>  雖然`volatile`提升可以用於 x86 和 x64，這些額外的屬性上實作受限的形式執行緒間通訊的某些屬性並不足夠實作間執行緒通訊一般。 C + + 標準建議，改為使用適當的同步處理原始物件來實作這類通訊。

不同平台可能以不同的方式表示這些類型的行為，因為移植平台之間的軟體很困難且 bug 容易取決於其特定的平台的行為。 雖然許多這類行為，可以觀察到，而且可能會出現穩定，依賴它們是至少不可移植，並在未定義或未指定行為的情況下，也會是錯誤。 即使在這份文件中所提到的行為不應依賴上，也無法在未來變更的編譯器或 CPU 的實作。

## <a name="example-migration-issues"></a>範例移轉問題

這份文件的其餘部分說明如何不同的行為，這些 c + + 語言項目可以產生不同的結果不同平台上。

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>不帶正負號的整數的浮點轉換

在 ARM 架構，浮點值轉換為 32 位元整數飽和到接近如果浮點數的值超出範圍時，可以表示的整數，可以代表整數的值。 在 x86 和 x64 架構轉換繞如果整數是不帶正負號，或如果已簽署的整數設定為-2147483648。 沒有這些架構直接支援浮點值的轉換為較小的整數類型。不過，32 位元，會進行轉換，而且結果會截斷成較小的大小。

對於 ARM 架構，表示它飽和的 32 位元整數，但產生的值大於截斷的結果時，轉換成不帶正負號的類型正確飽和較小的帶正負號的類型飽和度和截斷的組合作業的完整的 32 位元整數，較小的類型可以表示但太小。 轉換也飽和正確的 32 位元帶正負號的整數，但飽和、 帶正負號整數的截斷所產生的正面飽和值-1 和負面飽和的值為 0。 較小的帶正負號整數的轉換會產生無法預期的已截斷的結果。

X86 和 x64 架構的循環的不帶正負號的整數轉換的行為與帶正負號的整數轉換發生截斷，連同溢位的明確價值的組合進行大部分的排班的結果是否無法預期太大。

這些平台也不同 NaN (Not a Number) 轉換成整數類型的處理方式。 在 ARM，NaN 將轉換為 0x00000000;在 x86 和 x64，轉換為 0x80000000。

浮點轉換只要求上，如果您知道值會轉換成整數類型的範圍內。

### <a name="shift-operator---behavior"></a>移位運算子 (\< \< >>) 行為

在 ARM 架構中，值可以移位 left 或 right 最多 255 位元模式開始，重複前。 在 x86 和 x64 架構上圖樣的重複在每個倍數 32 除非模式的來源是 64 位元變數。在此情況下，在每個 64 的倍數上 x64 和 x86，其中運用軟體實作上 256 的每個倍數相同的模式。 比方說，針對 32 位元變數具有 32 的位置向左移位 1 的值，ARM 上，則結果為 0、 在 x86 上的結果會是 1，和在 x64 上的結果也是 1。 不過，如果值的來源是 64 位元變數，然後所有三個平台上的結果為 4294967296，而值不會 「 循環 」 直到它已在 x64 或 256 位置 on ARM 和 x86 上移 64 的位置。

超過來源類型中的位元的數字的移位運算的結果是未定義的因為編譯器不需要在所有情況下有一致的行為。 比方說，如果在編譯時期已知的排班的兩個運算元，編譯器可能最佳化程式使用內部常式預先計算排班的結果，並再替代取代移位運算的結果。 如果移位量太大，或負數，內部常式的結果可能不同於相同的 shift 運算式的結果執行的 cpu。

### <a name="variable-arguments-varargs-behavior"></a>變數引數 (varargs) 的行為

在 ARM 架構中，從變數引數清單會在堆疊傳遞的參數受限於對齊方式。 例如，64 位元參數在 64 位元界限上對齊。 在 x86 和 x64 中，會在堆疊傳遞的引數受限於未對齊和組件緊密。 這項差異可能會導致 variadic 函式，例如`printf`讀取要用做為填補字元在 ARM 上如果預期的變數引數清單的配置不符合，即使它可能適用於某些值的子集，在 x86 上的記憶體位址或 x64 架構。 請考量以下範例：

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

在此情況下，藉由確定使用正確的格式規格時修正 bug 以便會被視為引數的對齊方式。 此程式碼正確：

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>引數評估順序

因為 ARM、 x86，和 x64 處理器的不同，因此，它們可以在不同的需求，編譯器實作，以及不同最佳化的機會。 基於此原因，以及其他因素，例如呼叫慣例和最佳化設定，編譯器可能會評估函式引數，不同的順序在不同的架構或其他因素的變更時。 這會造成應用程式依賴特定評估順序意外變更行為。

函式引數會影響其他在相同的呼叫函式的引數的副作用，就會發生這種錯誤。 通常這種相依性是容易避免，但是它可以有時會遮住很難分辨，相依性或運算子多載。 這個程式碼範例，請考慮：

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

這會顯示完整定義，但是如果`->`和`*`不多載的運算子，則此程式碼會轉譯為項目看起來像這樣：

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

如果沒有之間的相依性和`operator->(memory_handle)`和`operator*(p)`、 程式碼可能依賴特定評估順序，即使原始的程式碼看起來像是沒有任何可能的相依性。

### <a name="volatile-keyword-default-behavior"></a>volatile 關鍵字的預設行為

MSVC 編譯器支援的兩個不同的方式解讀`volatile`您可以使用編譯器參數指定的儲存體限定詞。 [/Volatile: ms](../build/reference/volatile-volatile-keyword-interpretation.md)參數選取 Microsoft 擴充變動性保證強式排序的語意，因為已經過傳統情況適用於 x86 和 x64，因為這些架構的強式記憶體模型。 [/Volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)參數選取嚴格 c + + 標準動態語意，不保證強式排序。

預設值是在 ARM 架構上**/volatile:iso**因為 ARM 處理器需要弱式排序記憶體模型，以及因為 ARM 軟體沒有舊版的信賴憑證者的擴充語意**/volatile: ms**而且通常不需要與軟體進行互動。 不過，它是仍有時方便或甚至不必編譯 ARM 程式來使用擴充的語意。 例如，可能是移植程式能夠使用 ISO c + + 語意的成本太高或驅動程式軟體可能要遵守的傳統的語意，才能正確運作。 在這些情況下，您可以使用**/volatile: ms**參數; 不過，若要重新建立 ARM 目標的傳統變動性的語意，編譯器必須插入周圍每個讀取或寫入的記憶體屏障`volatile`變數，以強制執行強式的順序，這可能對效能造成負面影響。

在 x86 和 x64 架構的預設值是**/volatile: ms**因為大部分的軟體，已經建立這些架構使用 MSVC 依賴。 當您編譯 x86 和 x64 的程式時，您可以指定**/volatile:iso**參數以避免不必要依賴傳統變動性的語意，並將可攜性。

## <a name="see-also"></a>另請參閱

[針對 ARM 處理器設定 Visual C++](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
