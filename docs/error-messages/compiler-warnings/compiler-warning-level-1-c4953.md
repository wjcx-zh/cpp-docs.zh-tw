---
title: 編譯器警告 （層級 1） C4953 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e53808d4ad97bad4eccdf81b0a863277f8f7796
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194628"
---
# <a name="compiler-warning-level-1-c4953"></a>編譯器警告 (層級 1) C4953

> 內嵌項 '*函式*' 已經編輯，因為已收集的分析資料，未使用的設定檔資料

使用時[除了](../../build/reference/ltcg-link-time-code-generation.md)，編譯器偵測到輸入的模組之後已重新編譯`/LTCG:PGINSTRUMENT`的函式 (*函式*) 的已編輯，其中，現有的測試執行已識別函式的候選項目為內嵌。 不過，重新編譯模組之後，函式就不再是進行內嵌的候選項目。

這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，則這個警告會變成錯誤。