---
title: 編譯器警告 （層級 1） C4124 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a69190487c22987ead2d00ec102785ed42ea93c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090921"
---
# <a name="compiler-warning-level-1-c4124"></a>編譯器警告 （層級 1） C4124

__fastcall 與堆疊檢查是效率不佳

`__fastcall`關鍵字已使用與堆疊檢查已啟用。

`__fastcall`慣例產生更快的程式碼，但堆疊檢查會導致較慢的程式碼。 使用時`__fastcall`，關閉使用中檢查堆疊**check_stack** pragma 或 /Gs。

只會針對這些情況下宣告的第一個函式，會發出這個警告。