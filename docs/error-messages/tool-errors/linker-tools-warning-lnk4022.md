---
title: 連結器工具警告 LNK4022 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 644e7a9ba26dab15e2bfa2a269f62c04f0510180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040995"
---
# <a name="linker-tools-warning-lnk4022"></a>連結器工具警告 LNK4022

找不到符號 'symbol' 的唯一相符項目

連結或 LIB 找到多個比對指定的未裝飾符號，並無法解析模稜兩可。 會不產生任何輸出檔案 （.exe、.dll、.exp 或.lib）。 這個警告後面接著一個警告[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)每個重複的符號，且最後後面嚴重錯誤[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。

若要避免這個警告，指定以其裝飾形式的符號。 執行[DUMPBIN](../../build/reference/dumpbin-options.md)上的物件，以檢視裝飾名稱。