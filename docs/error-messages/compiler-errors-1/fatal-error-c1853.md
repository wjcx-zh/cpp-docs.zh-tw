---
title: 嚴重錯誤 C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 30cf003cc81cb27f7c68b7f0a38529e2d9c88ef5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677821"
---
# <a name="fatal-error-c1853"></a>嚴重錯誤 C1853

> '*filename*' 先行編譯標頭檔從舊版的編譯器，或者先行編譯標頭是 c + +，而先使用從 C （反之亦然）

可能的原因：

- 先行編譯標頭已與先前的編譯器版本進行編譯。 請嘗試重新編譯的標頭，使用目前的編譯器。

- 先行編譯標頭是 c + +，而您使用它從 c 與 C 搭配使用的標頭所指定的其中一個[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項，或將來源檔案的後置詞變更為"c"。 如需詳細資訊，請參閱 <<c0> [ 先行編譯的程式碼的兩個選擇](../../build/reference/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。