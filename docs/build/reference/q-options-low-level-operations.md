---
title: /Q 選項 (低階運算)
ms.date: 01/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 6348226aa38d1f2eefdf9e19e27c4c87bd2f0812
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927662"
---
# <a name="q-options-low-level-operations"></a>/Q 選項 (低階運算)

您可以使用 **/q**編譯器選項來執行下列低層級編譯器作業：

- [/Qfast_transcendentals （強制快速超越函式）](qfast-transcendentals-force-fast-transcendentals.md)：產生快速超越函式。

- [/QIfist （隱藏 _ftol）](qifist-suppress-ftol.md)：當`_ftol`需要從浮點類型轉換為整數類型時，會隱藏（僅限 x86）。

- [/Qimprecise_fwaits （移除 Try 區塊內的 try 區域 fwaits）](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)：移除 `fwait` 區塊內的 `try` 命令。

- [/Qpar （自動平行化工具）](qpar-auto-parallelizer.md)：啟用標記為 [#pragma loop()](../../preprocessor/loop.md) 指示詞之迴圈的自動平行處理。

- [/Qpar-report （自動平行化工具報告層級）](qpar-report-auto-parallelizer-reporting-level.md)：啟用自動平行處理的報告層級。

- [/Qsafe_fp_loads](qsafe-fp-loads.md)：隱藏浮點暫存器載入的優化，以及在記憶體和 MMX 暫存器之間移動的功能。

- [/Qspectre](qspectre.md)：產生指示，以減輕某些 Spectre 的安全性弱點。

- [/Qvec-report （自動向量化工具報告層級）](qvec-report-auto-vectorizer-reporting-level.md)：啟用自動向量化的報告層級。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
