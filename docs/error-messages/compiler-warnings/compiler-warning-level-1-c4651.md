---
title: 編譯器警告 （層級 1） C4651 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b516ef86372901d00dd20d94ed10d5e361bbab8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099459"
---
# <a name="compiler-warning-level-1-c4651"></a>編譯器警告 (層級 1) C4651

[定義] 指定先行編譯標頭，但不適用於目前的編譯

指定定義時所產生先行編譯標頭，但不是在此編譯中。

定義將會生效內先行編譯標頭，而不是在程式碼的其餘部分。

如果先行編譯標頭不在建置 /DSYMBOL，編譯器會產生這個警告如果 /Yu 編譯沒有 /DSYMBOL。  /Yu 命令列中加入 /DSYMBOL 可以解決這個警告。