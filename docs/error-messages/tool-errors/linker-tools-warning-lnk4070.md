---
title: 連結器工具警告 LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622972"
---
# <a name="linker-tools-warning-lnk4070"></a>連結器工具警告 LNK4070

/Out: filename 中的指示詞。EXP 與輸出檔名 'filename';忽略指示詞

`filename`中指定[名稱](../../build/reference/name-c-cpp.md)或[程式庫](../../build/reference/library.md).exp 檔案建立時的陳述式與輸出`filename`，已預設或指定了[/Out](../../build/reference/out-output-file-name.md)選項。

如果您變更輸出檔案在開發環境中和未更新專案的.def 檔的名稱，您會看到這個警告。 手動更新.def 檔案，以解決這個警告。

使用產生的 DLL 的用戶端程式可能會遇到的問題。