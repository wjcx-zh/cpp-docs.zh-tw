---
title: /Q 選項 (低階運算)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: f5342071cef76bcc736f128c344279898a61c462
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231490"
---
# <a name="q-options-low-level-operations"></a>/Q 選項 (低階運算)

您可以使用 **/q**編譯器選項來執行下列低層級編譯器作業：

- [/Qfast_transcendentals （強制快速超越函式）](qfast-transcendentals-force-fast-transcendentals.md)：產生快速超越函式。

- [/QIfist （隱藏 _ftol）](qifist-suppress-ftol.md)：在 `_ftol` 需要從浮點類型轉換為整數類型（僅限 x86）時隱藏。

- [/Qimprecise_fwaits （移除 Try 區塊內的 try 區域 fwaits）](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)：移除 `fwait` **`try`** 區塊內的命令。

- [/QIntel-jcc-erratum](qintel-jcc-erratum.md)：降低 Intel 跳躍條件程式碼（jcc）錯誤微碼更新所造成的效能影響。

- [/Qpar （自動平行化工具）](qpar-auto-parallelizer.md)：啟用以[#pragma loop （）](../../preprocessor/loop.md)指示詞標記的迴圈自動平行處理。

- [/Qpar-report （自動平行化工具報告層級）](qpar-report-auto-parallelizer-reporting-level.md)：啟用自動平行處理的報告層級。

- [/Qsafe_fp_loads](qsafe-fp-loads.md)：隱藏浮點暫存器載入的優化，以及在記憶體和 MMX 暫存器之間移動的功能。

- [/Qspectre](qspectre.md)：產生用來減輕特定 Spectre 安全性弱點的指示。

- [/Qspectre-load](qspectre-load.md)：產生指示，以根據負載來降低 Spectre 的安全性弱點。

- [/Qspectre-load-cf](qspectre-load-cf.md)：根據載入的控制流程指示，產生可減輕 Spectre 安全性弱點的指示。

- [/Qvec-report （自動向量化工具報告層級）](qvec-report-auto-vectorizer-reporting-level.md)：啟用自動向量化的報告層級。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
