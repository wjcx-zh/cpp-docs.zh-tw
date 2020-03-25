---
title: 嚴重錯誤 C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204187"
---
# <a name="fatal-error-c1081"></a>嚴重錯誤 C1081

' symbol '：檔案名太長

檔案路徑名稱的長度超過 `_MAX_PATH` （由 STDLIB.H> 定義為260個字元）。 請縮短檔案名。

如果您使用簡短的檔案名來呼叫 CL，編譯器可能需要產生完整的路徑名稱。 例如，`cl -c myfile.cpp` 可能會導致編譯器產生：

```
D:\<very-long-directory-path>\myfile.cpp
```
