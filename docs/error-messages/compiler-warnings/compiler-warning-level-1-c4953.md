---
title: 編譯器警告 (層級 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1948342e1ff97c38ca3a44694dc7e7d399d96825
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568035"
---
# <a name="compiler-warning-level-1-c4953"></a>編譯器警告 (層級 1) C4953

> 內嵌項 '*函式*' 已經編輯，因為已收集的分析資料，未使用的設定檔資料

使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器在 `/LTCG:PGINSTRUMENT` 後面偵測到重新編譯過的輸入模組，並且具有編輯過的函式 (*function*)，在其中，現有測試執行會將函式視為進行內嵌的候選項目。 不過，重新編譯模組之後，函式就不再是進行內嵌的候選項目。

這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，則這個警告會變成錯誤。