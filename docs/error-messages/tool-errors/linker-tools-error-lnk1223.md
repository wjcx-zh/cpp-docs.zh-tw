---
title: 連結器工具錯誤 LNK1223 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8639919c74559829367108b36d62594e2a83a91a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067977"
---
# <a name="linker-tools-error-lnk1223"></a>連結器工具錯誤 LNK1223

檔案無效或損毀：檔案包含無效的 .pdata 比重

針對使用 pdata 的 RISC 平台，如果編譯器發出的 .pdata 區段具有未排序的項目，會發生這個錯誤。

若要修正此問題，請嘗試編譯時不要[/GL （整個程式最佳化）](../../error-messages/tool-errors/linker-tools-error-lnk1223.md)啟用。 空白的函式主體也可能在某些情況下導致此錯誤。