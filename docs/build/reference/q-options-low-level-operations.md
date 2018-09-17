---
title: -Q 選項 （低階運算） |Microsoft Docs
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /q
dev_langs:
- C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15854333a9f26f87d20f7819327e68050ab37bf6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717770"
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
