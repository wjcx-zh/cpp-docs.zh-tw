---
title: 嚴重錯誤 C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: ec2d6bf6bac46cca8bdc2e3b8fe7cc6b7799d78a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820724"
---
# <a name="fatal-error-c1853"></a>嚴重錯誤 C1853

> '*filename*' 先行編譯標頭檔從舊版的編譯器，或者先行編譯標頭是 c + +，而先使用從 C （反之亦然）

可能的原因：

- 先行編譯標頭已與先前的編譯器版本進行編譯。 請嘗試重新編譯的標頭，使用目前的編譯器。

- 先行編譯標頭是 c + +，而您使用它從 c 與 C 搭配使用的標頭所指定的其中一個[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)編譯器選項，或將來源檔案的後置詞變更為"c"。 如需詳細資訊，請參閱 <<c0> [ 先行編譯的程式碼的兩個選擇](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code)。