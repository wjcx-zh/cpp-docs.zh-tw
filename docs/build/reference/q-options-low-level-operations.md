---
title: "-Q 選項 （低階運算） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d970c2de5e34840ab2ed77f229c329db3c6f72fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="q-options-low-level-operations"></a>/Q 選項 (低階運算)
您可以使用**/Q**編譯器選項來執行下列低階編譯器運算：  
  
-   [/Qfast_transcendentals （強制快速超越函式）](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)： 產生快速超越函式。  
  
-   [/Qifist (抑制 _ftol)](../../build/reference/qifist-suppress-ftol.md)： 隱藏`_ftol`從浮點類型轉換為整數類型時需要 (只顯示 x86)。  
  
-   [/Qimprecise_fwaits （移除內的 fwaits 再試一次）](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)： 移除`fwait`命令內`try`區塊。  
  
-   [/Qpar （自動平行化工具）](../../build/reference/qpar-auto-parallelizer.md)： 啟用自動平行處理迴圈，以標記[#pragma loop （)](../../preprocessor/loop.md)指示詞。  
  
-   [/Qpar-report （自動平行化工具報告層級）](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)： 啟用自動平行處理的報告層級。  
  
-   [/Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md)： 隱藏最佳化的浮點暫存器載入及記憶體和 MMX 之間移動的註冊。  
  
-   [/Qvec-report （自動向量化工具報告層級）](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)： 啟用自動向量化的報告層級。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)