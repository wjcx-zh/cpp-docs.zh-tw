---
title: "浮點數的移轉問題 | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59898a5ad6af6728b16163c766f6295c850dc577
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="floating-point-migration-issues"></a>浮點數的移轉問題  
  
有時候，當您將專案升級至較新版本的 Visual Studio 時，可能會發現某些浮點運算的結果已變更。 這通常是因下列兩個原因之一所導致：由於產生程式碼的變更充分利用可用的處理器，以及 C 執行階段程式庫 (CRT) 中用於數學函式的演算法有 Bug 修正或變更。 一般來說，新的結果會在語言標準所指定的限制範圍內，因此是正確的。 請繼續閱讀以了解變更的項目，以及如何取得之前函式所得的相同結果 (若有必要的話)。  

## <a name="new-math-functions-and-universal-crt-changes"></a>新的數學函式和通用的 CRT 變更  
  
好幾年來，Visual Studio 就已提供大多數的 CRT 數學函式，但是自 Visual Studio 2013 起，才包含所有 ISO C99 所需的函式。 實作這些函式可以平衡效能與正確性。 因為要在每個情況中產生正確的四捨五入結果可能極為昂貴，所以這些函式會設計成有效率產生最接近正確四捨五入結果的近似值。 在大部分情況下，產生的結果是在正確四捨五入結果的 +/-1 *ulp* 內，但也可能出現較大的誤差。 如果您之前是使用不同的數學程式庫來取得這些函式，則結果的變更可能是因為實作差異導致。   
    
在將數學函式移至 Visual Studio 2015 的通用 CRT 時，即已使用一些新的演算法，並將於 Visual Studio 2013 新發現的數個函式實作 Bug 加以修正。 如果浮點數計算是使用這些函式，這些變更可能會導致計算結果出現可偵測到的差異。 有 Bug 問題的函式是 erf、exp2、remainder、remquo、scalbln、scalbn 及其浮點與長雙精度的變化。  Visual Studio 2015 的其他變更已修正保留浮點數狀態文字時發生的問題，以及 _clear87、_clearfp、fegetenv、fesetenv 和 feholdexcept 函式例外狀況的狀態資訊問題。  
  
## <a name="processor-differences-and-compiler-flags"></a>處理器的差異和編譯器旗標  
  
許多浮點數學程式庫函式對不同的 CPU 架構會有不同的實作。 例如，32 位元 x86 CRT 的實作可能和 64 位元 x64 CRT 的實作不同。 此外，某些函式對指定的 CPU 架構可能有多種實作。 在執行階段，會根據 CPU 支援的指令集動態選取最有效率的實作。 例如，在 32 位元 x86 CRT，有些函式同時有 x87 實作和 SSE2 實作。 在支援 SSE2 的 CPU 上執行時，會使用較快的 SSE2 實作。 在不支援 SSE2 的 CPU 上執行時，會使用較慢的 x87 實作。 您可能會在移轉舊版程式碼時看到這種情況，因為 Visual Studio 2012 已將預設 x86 編譯器架構選項變更為 [/arch:SSE2](../build/reference/arch-x86.md)。 由於數學程式庫函式的不同實作可能會使用不同的 CPU 指令和不同的演算法來產生結果，因此函式在不同的平台中可能會產生不同的結果。 在大部分情況下，結果是在正確四捨五入結果的 +/-1 ulp 內，但實際的結果可能因 CPU 而異。  
  
相較於舊程式碼與新程式碼來看，即使是使用相同編譯器旗標，Visual Studio 不同浮點數模式的程式碼產生正確性增強功能，也可能影響浮點數運算的結果。 例如，在指定 [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md) (預設值) 或 **/fp:strict** 時，Visual Studio 2010 所產生的程式碼可能並未正確透過運算式來傳播中繼的非數字 (NaN) 值。 因此，如果某些運算式是在舊版編譯器中提供數值結果，現在即可正確產生 NaN 結果。 您可能也會發覺到差異，因為針對 **/fp:fast** 啟用的程式碼最佳化現可利用更多的處理器功能。 這些最佳化可以使用較少的指示，但或許會影響產生的結果，因為系統已移除部分先前可見的中繼作業。  
  
## <a name="how-to-get-identical-results"></a>如何取得相同的結果  
  
在大部分情況下，最新的編譯器和程式庫中的浮點數變更可帶來更快及/或更正確的行為。 當 SSE2 指示取代 x87 指示時，您甚至可能會發覺更好的處理器電源效能。 但是，如果您的程式碼必須精確地複寫舊版編譯器的浮點數行為，請考慮使用 Visual Studio 原生多目標功能，並使用舊版工具組來建置受影響的專案。 如需詳細資訊，請參閱[在 Visual Studio 中使用原生多目標來建置舊專案](use-native-multi-targeting.md)。  
  
## <a name="see-also"></a>另請參閱  
  
[從舊版的 Visual C++ 升級專案](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[潛在升級問題概觀 (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Visual C++ 變更歷程記錄 2003 - 2015](visual-cpp-change-history-2003-2015.md)  
