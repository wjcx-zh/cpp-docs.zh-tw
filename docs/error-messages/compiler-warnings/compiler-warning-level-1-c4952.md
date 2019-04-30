---
title: 編譯器警告 (層級 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: c2e9b88125655d9ea0abe3e65500b149289ba83b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393281"
---
# <a name="compiler-warning-level-1-c4952"></a>編譯器警告 (層級 1) C4952

> '*函式*': 在程式資料庫中找到的任何設定檔資料'*pgd_file*'

使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)時，編譯器偵測到輸入模組在 `/LTCG:PGINSTRUMENT` 之後經過重新編譯，且出現新的函式 ()。

這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，則這個警告會變成錯誤。