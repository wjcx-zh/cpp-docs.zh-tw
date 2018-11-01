---
title: NMAKE 嚴重錯誤 U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: ddf1d262fb8dfc6e63b0bf5cc098b7b140539310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641502"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE 嚴重錯誤 U1051

記憶體不足

NMAKE 已用盡記憶體，包括虛擬記憶體，因為 makefile 太大或太複雜。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 釋放一些磁碟空間。

1. 增加 Windows NT 分頁檔或 Windows 分頁檔的大小。

1. 如果只使用 makefile 的一部分，請 makefile 分成不同的檔案，或使用 **！如果**前置處理器指示詞來限制 NMAKE 必須處理的數量。 **！如果**指示詞包含 **！如果**， `!IFDEF`， **！IFNDEF**， **！ELSE IF**， **！ELSE** `IFDEF`，和 **！ELSE** `IFNDEF`。