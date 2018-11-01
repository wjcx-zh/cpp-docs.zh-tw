---
title: /Q 選項 (低階運算)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: a6dcbd256fa3510955884d3adba4855b23cdbfab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514243"
---
# <a name="q-options-low-level-operations"></a>/Q 選項 (低階運算)

您可以使用 **/Q**編譯器選項來執行下列低階編譯器運算：

- [/Qfast_transcendentals （強制快速超越函式）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)： 產生快速超越函式。

- [/Qifist (抑制 _ftol)](../../build/reference/qifist-suppress-ftol.md)： 會隱藏`_ftol`從浮點類型轉換為整數型別時需要 (僅限顯示 x86)。

- [/Qimprecise_fwaits （移除 Try 區域 fwaits 內）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)： 移除`fwait`內的命令`try`區塊。

- [/Qpar （自動平行化工具）](../../build/reference/qpar-auto-parallelizer.md)： 啟用自動平行處理迴圈標記[#pragma loop （)](../../preprocessor/loop.md)指示詞。

- [/Qpar-report （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)： 啟用自動平行處理的報告層級。

- [/Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)： 抑制浮點暫存器載入，並針對移動之間的記憶體和 MMX 暫存器的最佳化。

- [/Qspectre](../../build/reference/qspectre.md)： 將會產生以減少特定 Spectre 安全性弱點的指示。

- [/Qvec-report （自動向量化工具報告層級）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)： 啟用自動向量化的報告層級。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
