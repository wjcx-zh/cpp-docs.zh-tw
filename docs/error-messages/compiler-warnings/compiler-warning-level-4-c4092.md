---
title: 編譯器警告 （層級 4） C4092
ms.date: 11/04/2016
f1_keywords:
- C4092
helpviewer_keywords:
- C4092
ms.assetid: 396ae826-a892-4327-bd66-f4762376d72b
ms.openlocfilehash: a6949586cf3faa00aafed37a72e58c1b80266cf5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490411"
---
# <a name="compiler-warning-level-4-c4092"></a>編譯器警告 （層級 4） C4092

sizeof 傳回 'unsigned long'

運算元`sizeof`運算子是非常大，因此`sizeof`傳回不帶正負號**長**。 Microsoft 擴充功能下會發生這個警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。 ANSI 相容性 (/Za)，結果會改為截斷。