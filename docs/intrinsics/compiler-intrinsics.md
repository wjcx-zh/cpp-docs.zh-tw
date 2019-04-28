---
title: 編譯器內建
ms.date: 11/04/2016
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 9a014e870d731d7e7d443c3bfefd66884aa50d5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349104"
---
# <a name="compiler-intrinsics"></a>編譯器內建

大部份的函式都包含在程式庫中，但有些函式是內建 (也就是內建) 到編譯器。 這些稱為內建函式或內建。

## <a name="remarks"></a>備註

如果函式是內建的，則該函式的程式碼通常是以內嵌方式插入，避免函式呼叫的額外負荷，並可針對該函式發出高效率的機器指令。 內建函式經常比對等的內嵌組件來得快，因為最佳化工具具有內建知識，知道有多少內建函式在運作，因此可以使用在使用內嵌組件時無法使用的某些最佳化。 此外，最佳化工具可以用不同方式擴充內建函式、以不同方式對齊緩衝區，或是根據呼叫的內容和引數進行其他調整。

使用內建函式會影響程式碼的可攜性，因為如果程式碼是使用其他編譯器所編譯，Visual C++ 中可用的內建函式可能無法使用，而且在某些目標架構中可能可用的某些內建函式，對於所有架構會無法使用。 然而，內建函式的可攜性通常高於內嵌組件。 在不支援內嵌組件的 64 位元架構上必須有內建函式。

某些內建函式 (如 `__assume` 和 `__ReadWriteBarrier`) 會提供資訊給編譯器，這會影響最佳化工具的行為。

某些內建函式僅以內建函式的形式提供使用，而有些內建函式則是在函式和內建實作中都提供使用。 您可以指示編譯器以兩種方式之一使用內建實作，取決於您是只要啟用特定的函式，還是想要啟用所有的內建函式。 第一種方式是使用`#pragma intrinsic(`*內建函式-名稱-清單*`)`。 Pragma 可以用來指定單一內建函式或以逗號分隔的多個內建函式。 第二個是使用[/Oi （產生內建函式）](../build/reference/oi-generate-intrinsic-functions.md)編譯器選項，可在指定的平台的所有內建函式。 底下 **/Oi**，使用`#pragma function(`*內建函式-名稱-清單*`)`強制使用而不是內建函式呼叫。 如果特定內建的文件資訊，此常式僅可作為內建，則會使用內建函式的實作，不論 **/Oi**或`#pragma intrinsic`指定。 在所有情況下， **/Oi**或`#pragma intrinsic`允許，但不會強制，最佳化工具使用內建函式。 最佳化工具仍然可以呼叫該函式。

某些標準的 C/C++ 程式庫函式可作為某些架構上的內建實作使用。 如果，在呼叫 CRT 函式時，會使用內建函式實作 **/Oi**命令列上指定。

標頭檔， \<intrin.h >，是可宣告通用內建函式的原型。 製造商特定內建函式位於\<immintrin.h> > 和\<ammintrin.h > 標頭檔。 此外，某些 Windows 標頭宣告對應到編譯器內建函式上的函式。

下列各節會列出各種架構上可用的所有內建函式。 如需有關內建函式在特定目標處理器上之運作方式的詳細資訊，請參閱製造商的參考文件。

- [ARM 內建](../intrinsics/arm-intrinsics.md)

- [x86 內建清單](../intrinsics/x86-intrinsics-list.md)

- [x64 (amd64) 內建清單](../intrinsics/x64-amd64-intrinsics-list.md)

- [所有架構可用的內建](../intrinsics/intrinsics-available-on-all-architectures.md)

- [依字母順序列出的內建函式](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>另請參閱

[ARM 組譯工具參考](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft 巨集組譯工具參考](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)