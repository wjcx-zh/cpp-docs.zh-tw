---
title: 編譯器錯誤 C2410 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4c2b57bcae062ccf811e33cf1deaea45f83737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052448"
---
# <a name="compiler-error-c2410"></a>編譯器錯誤 C2410

'identifier': 'context' 中的模稜兩可的成員名稱

識別碼是一個以上的結構或等位在此內容中的成員。

使用造成錯誤的運算元是結構或等位的規範。 結構或等位的規範是識別項的型別`struct`或是`union`(`typedef`名稱或變數中的結構或等位正在參考相同的型別)。 規範必須是要使用運算元的第一個成員選取運算子 （.） 的左的運算元。