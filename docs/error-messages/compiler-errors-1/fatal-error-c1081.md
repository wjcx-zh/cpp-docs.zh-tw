---
title: 嚴重錯誤 C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: f3c9f9bde5da7fb120accbb9a8d72e5715ab9d2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569665"
---
# <a name="fatal-error-c1081"></a>嚴重錯誤 C1081

'symbol': 檔名太長

檔案路徑名稱長度超過`_MAX_PATH`（定義由 STDLIB.h 為 260 個字元）。 請縮短檔案的名稱。

如果您具有短的檔名呼叫 CL.exe，可能需要編譯器產生完整路徑名稱。 比方說，`cl -c myfile.cpp`可能會導致編譯器產生：

```
D:\<very-long-directory-path>\myfile.cpp
```