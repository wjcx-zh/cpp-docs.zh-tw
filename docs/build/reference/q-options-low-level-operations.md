---
title: /Q 選項 (低階運算)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 5bbb63b4f437f8aefd5c84c1c1c4bd20bdb965cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319391"
---
# <a name="q-options-low-level-operations"></a>/Q 選項 (低階運算)

您可以使用 **/Q**編譯器選項來執行下列低階編譯器運算：

- [/Qfast_transcendentals （強制快速超越函式）](qfast-transcendentals-force-fast-transcendentals.md):產生快速超越函式。

- [/Qifist （抑制 _ftol）](qifist-suppress-ftol.md):隱藏`_ftol`從浮點類型轉換為整數型別時需要 (僅限顯示 x86)。

- [/Qimprecise_fwaits （移除 Try 區域 fwaits 內）](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md):移除 `fwait` 區塊內的 `try` 命令。

- [/Qpar （自動平行化工具）](qpar-auto-parallelizer.md):啟用標記為 [#pragma loop()](../../preprocessor/loop.md) 指示詞之迴圈的自動平行處理。

- [/Qpar-report （自動平行化工具報告層級）](qpar-report-auto-parallelizer-reporting-level.md):啟用自動平行處理的報告層級。

- [/Qsafe_fp_loads](qsafe-fp-loads.md):抑制浮點暫存器載入，並針對記憶體和 MMX 暫存器之間移動的最佳化。

- [/Qspectre](qspectre.md):會產生以減少特定 Spectre 安全性弱點的指示。

- [/Qvec-report （自動向量化工具報告層級）](qvec-report-auto-vectorizer-reporting-level.md):啟用自動向量化的報告層級。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
