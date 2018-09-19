---
title: 連結器工具錯誤 LNK2008 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eda06e7f133ada4de1b7ec28ac21be205a71f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086807"
---
# <a name="linker-tools-error-lnk2008"></a>連結器工具錯誤 LNK2008

修復目標不是對齊 'symbol_name'

連結您未正確對齊的目的檔中找到修復目標。

此錯誤可能因自訂 secton 對齊方式 (例如 #pragma [pack](../../preprocessor/pack.md))，[對齊](../../cpp/align-cpp.md)修飾詞，或使用組件語言程式碼，以修改 secton 對齊方式。

如果您的程式碼不會使用上述任一種，原因可能是由編譯器。