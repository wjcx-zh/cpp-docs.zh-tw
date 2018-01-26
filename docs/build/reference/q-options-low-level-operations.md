---
title: "-Q 選項 （低階運算） |Microsoft 文件"
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /q
dev_langs: C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7636b042669c7f7b04d2bc662bcaa2fbe4bdc82a
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="q-options-low-level-operations"></a>/Q 選項 (低階運算)

您可以使用**/Q**編譯器選項來執行下列低階編譯器運算：

- [/Qfast_transcendentals （強制快速超越函式）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)： 產生快速超越函式。

- [/Qifist (抑制 _ftol)](../../build/reference/qifist-suppress-ftol.md)： 隱藏`_ftol`從浮點類型轉換為整數類型時需要 (只顯示 x86)。

- [/Qimprecise_fwaits （移除內的 fwaits 再試一次）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)： 移除`fwait`命令內`try`區塊。

- [/Qpar （自動平行化工具）](../../build/reference/qpar-auto-parallelizer.md)： 啟用自動平行處理迴圈，以標記[#pragma loop （)](../../preprocessor/loop.md)指示詞。

- [/Qpar-report （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)： 啟用自動平行處理的報告層級。

- [/Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)： 隱藏最佳化的浮點暫存器載入及記憶體和 MMX 之間移動的註冊。

- [/ Qspectre](../../build/reference/qspectre.md)： 產生以降低某些 Spectre 安全性弱點的指示。

- [/Qvec-report （自動向量化工具報告層級）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)： 啟用自動向量化的報告層級。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
