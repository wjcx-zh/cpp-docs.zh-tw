---
title: 編譯器警告 （層級 1） C4650 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d49b21452465f26d6e696f928c04c20dc0e33307
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052883"
---
# <a name="compiler-warning-level-1-c4650"></a>編譯器警告 (層級 1) C4650

不在先行編譯標頭; 中的偵錯資訊只有全域符號標頭中的會提供

先行編譯標頭檔不是使用 Microsoft 符號偵錯資訊編譯。

連結時，產生的可執行檔或動態連結程式庫檔案不會包含先行編譯標頭中包含的本機符號的偵錯資訊。

重新編譯的先行編譯的標頭檔，也可以避免此警告[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令列選項。