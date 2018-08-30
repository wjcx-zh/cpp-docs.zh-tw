---
title: 編譯器警告 （層級 1） C4952 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f62f4c18380d89eb516a5fa49ef63e92ab79a6f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207147"
---
# <a name="compiler-warning-level-1-c4952"></a>編譯器警告 (層級 1) C4952

> '*函式*': 在程式資料庫中找到的任何設定檔資料'*pgd_file*'

使用時[除了](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到輸入的模組之後已重新編譯`/LTCG:PGINSTRUMENT`的新函式 (*函式*) 存在。

這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，則這個警告會變成錯誤。