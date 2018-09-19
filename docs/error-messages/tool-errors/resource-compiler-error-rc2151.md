---
title: 資源編譯器錯誤 RC2151 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a15f3f1237df9e4b706a2c2048dddd6d5db395d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109778"
---
# <a name="resource-compiler-error-rc2151"></a>資源編譯器錯誤 RC2151

無法重新使用字串常數

您要使用相同的值在兩次**STRINGTABLE**陳述式。 請確定您不會混淆重疊的十進位和十六進位值。

在每個識別碼**STRINGTABLE**必須是唯一的。 最高效率使用連續的常數，著手 16 的倍數。