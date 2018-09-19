---
title: 編譯器警告 （層級 4） C4092 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4092
dev_langs:
- C++
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84aa73120dabd261d54e764d1e0bfe8bc9c561a0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039601"
---
# <a name="compiler-warning-level-4-c4092"></a>編譯器警告 （層級 4） C4092

sizeof 傳回 'unsigned long'

運算元`sizeof`運算子是非常大，因此`sizeof`傳回不帶正負號**長**。 Microsoft 擴充功能下會發生這個警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 ANSI 相容性 (/Za)，結果會改為截斷。