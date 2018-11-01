---
title: 連結器工具錯誤 LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: 97bb2be18da5d166d1d5fba42e4ec8ce1f0439fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544218"
---
# <a name="linker-tools-error-lnk2008"></a>連結器工具錯誤 LNK2008

修復目標不是對齊 'symbol_name'

連結您未正確對齊的目的檔中找到修復目標。

此錯誤可能因自訂 secton 對齊方式 (例如 #pragma [pack](../../preprocessor/pack.md))，[對齊](../../cpp/align-cpp.md)修飾詞，或使用組件語言程式碼，以修改 secton 對齊方式。

如果您的程式碼不會使用上述任一種，原因可能是由編譯器。