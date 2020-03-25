---
title: 連結器工具警告 LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 391a477625b51fd37eacc5d455801ce90d2abbc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194001"
---
# <a name="linker-tools-warning-lnk4070"></a>連結器工具警告 LNK4070

/OUT：中的 filename 指示詞。EXP 與輸出檔案名 ' filename ' 不同;忽略指示詞

建立 .exp 檔案時，[名稱](../../build/reference/name-c-cpp.md)或連結[庫](../../build/reference/library.md)語句中所指定的 `filename`，會與預設假設或使用[/out](../../build/reference/out-output-file-name.md)選項指定的輸出 `filename` 不同。

如果您在開發環境中變更輸出檔案的名稱，而且未更新專案的 .def 檔案，就會看到這個警告。 手動更新 .def 檔案以解決此警告。

使用產生的 DLL 的用戶端程式可能會發生問題。
