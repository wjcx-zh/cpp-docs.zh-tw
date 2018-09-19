---
title: 嚴重錯誤 C1081 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b34f2f19a0bb8770ea9292fef120c415c0fb255a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060523"
---
# <a name="fatal-error-c1081"></a>嚴重錯誤 C1081

'symbol': 檔名太長

檔案路徑名稱長度超過`_MAX_PATH`（定義由 STDLIB.h 為 260 個字元）。 請縮短檔案的名稱。

如果您具有短的檔名呼叫 CL.exe，可能需要編譯器產生完整路徑名稱。 比方說，`cl -c myfile.cpp`可能會導致編譯器產生：

```
D:\<very-long-directory-path>\myfile.cpp
```