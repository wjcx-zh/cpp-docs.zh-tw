---
title: 連結器工具錯誤 LNK1164 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b07dcf360a58b07b84abe655641b758d6137d0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087422"
---
# <a name="linker-tools-error-lnk1164"></a>連結器工具錯誤 LNK1164

區段區段記憶體對齊 （數字） 大於 /ALIGN 值

目的檔中的指定區段的對齊方式大小超過指定的值[/對齊](../../build/reference/align-section-alignment.md)選項。 **/對齊**值必須是 2 的冪，且必須等於或超過目的檔中指定的區段對齊。

使用較小的區段記憶體對齊或增加可能是重新編譯 **/對齊**值。