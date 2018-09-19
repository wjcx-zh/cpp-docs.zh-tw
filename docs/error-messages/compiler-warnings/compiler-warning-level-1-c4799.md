---
title: 編譯器警告 （層級 1） C4799 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3d83917289e5ad76a874587894a66e163fed90a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088224"
---
# <a name="compiler-warning-level-1-c4799"></a>編譯器警告 (層級 1) C4799

> 在函式的結尾處沒有 EMMS '*函式*'

函式具有至少一個的 MMX 指令，但並沒有`EMMS`指令。 使用多媒體指令時，`EMMS`指示或`_mm_empty`內建函式應該也可用來清除多媒體的標記文字結尾的 MMX 程式碼。

當使用 ivec.h，指出程式碼不會正確地使用 execute EMMS 指令，在傳回之前，可能會收到 C4799。 這是這些標頭，則為 false 的警告。 您可能會關閉這些定義 _SILENCE_IVEC_C4799 ivec.h 中。 不過，請注意，這也會使編譯器無法為提供的這種類型的正確警告。

如需相關資訊，請參閱[Intel 的 MMX 指令集](../../assembler/inline/intel-s-mmx-instruction-set.md)。