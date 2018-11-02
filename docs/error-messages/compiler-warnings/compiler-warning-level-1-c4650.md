---
title: 編譯器警告 (層級 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536094"
---
# <a name="compiler-warning-level-1-c4650"></a>編譯器警告 (層級 1) C4650

不在先行編譯標頭; 中的偵錯資訊只有全域符號標頭中的會提供

先行編譯標頭檔不是使用 Microsoft 符號偵錯資訊編譯。

連結時，產生的可執行檔或動態連結程式庫檔案不會包含先行編譯標頭中包含的本機符號的偵錯資訊。

重新編譯的先行編譯的標頭檔，也可以避免此警告[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令列選項。