---
title: 資源編譯器錯誤 RC2151
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 8eaa50bc6080e37a4a74585eb03cbe4e40893bce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173440"
---
# <a name="resource-compiler-error-rc2151"></a>資源編譯器錯誤 RC2151

無法重新使用字串常數

您要使用相同的值在兩次**STRINGTABLE**陳述式。 請確定您不會混淆重疊的十進位和十六進位值。

在每個識別碼**STRINGTABLE**必須是唯一的。 最高效率使用連續的常數，著手 16 的倍數。