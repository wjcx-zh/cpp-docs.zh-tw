---
title: 連結器工具錯誤 LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 331521c357389c2f7c1aa786969154a2b747ffe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537955"
---
# <a name="linker-tools-error-lnk1223"></a>連結器工具錯誤 LNK1223

檔案無效或損毀：檔案包含無效的 .pdata 比重

針對使用 pdata 的 RISC 平台，如果編譯器發出的 .pdata 區段具有未排序的項目，會發生這個錯誤。

若要修正此問題，請嘗試編譯時不要[/GL （整個程式最佳化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)啟用。 空白的函式主體也可能在某些情況下導致此錯誤。