---
title: 連結器工具錯誤 LNK2023 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d8deaf8bfb10d3ceb56380560320ebb2cf9a7b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090317"
---
# <a name="linker-tools-error-lnk2023"></a>連結器工具錯誤 LNK2023

不正確的 dll 或進入點\<dll 或進入點 >

連結器將會載入 msobj90.dll 版本不正確。 請確定 link.exe 和 msobj90.dll 路徑中的有相同的版本。

Msobj90.dll 的相依性可能不存在。 Msobj90.dll 的相依性清單為：

- Msvcr90.dll

- Kernel32.dll

請檢查您的電腦可能已經過期的 msobj90.dll 的任何其他複本。