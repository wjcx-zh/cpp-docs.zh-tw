---
title: 連結器工具錯誤 LNK1200 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ecd51142bf30230b6b177a36e007345e93bf2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059312"
---
# <a name="linker-tools-error-lnk1200"></a>連結器工具錯誤 LNK1200

讀取程式資料庫 'filename' 時發生錯誤

無法讀取程式資料庫 (PDB)。

此錯誤的原因可能是檔案損毀。

如果`filename`是 PDB 物件檔案，重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。

如果`filename`PDB 的主要輸出檔，且累加連結期間發生此錯誤，刪除 PDB 並重新連結。