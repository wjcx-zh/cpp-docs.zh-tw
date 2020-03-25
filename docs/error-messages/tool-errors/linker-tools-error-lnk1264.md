---
title: 連結器工具錯誤 LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 00041e677ac7b69df9981551ee3b6cc18f9eb33d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183757"
---
# <a name="linker-tools-error-lnk1264"></a>連結器工具錯誤 LNK1264

/LTCG：指定了 PGINSTRUMENT，但不需要產生程式碼;檢測失敗

**/Ltcg：** 已指定 PGINSTRUMENT，但找不到使用[/gl](../../build/reference/gl-whole-program-optimization.md)編譯的 .obj 檔案。 檢測無法進行，且連結失敗。 命令列上必須至少有一個 .obj 檔案使用 **/gl**編譯，才能進行檢測。

特性指引優化（PGO）僅適用于64位編譯器。
