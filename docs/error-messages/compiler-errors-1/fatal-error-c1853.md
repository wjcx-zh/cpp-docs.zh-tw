---
title: 嚴重錯誤 C1853 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: error-reference
f1_keywords:
- C1853
dev_langs:
- C++
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 016e5bbf064643ddff0f63c5e16a967ed914f3e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044947"
---
# <a name="fatal-error-c1853"></a>嚴重錯誤 C1853

> '*filename*' 先行編譯標頭檔從舊版的編譯器，或者先行編譯標頭是 c + +，而先使用從 C （反之亦然）

可能的原因：

- 先行編譯標頭已與先前的編譯器版本進行編譯。 請嘗試重新編譯的標頭，使用目前的編譯器。

- 先行編譯標頭是 c + +，而您使用它從 c 與 C 搭配使用的標頭所指定的其中一個[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項，或將來源檔案的後置詞變更為"c"。 如需詳細資訊，請參閱 <<c0> [ 先行編譯的程式碼的兩個選擇](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。