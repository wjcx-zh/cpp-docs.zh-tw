---
title: 編譯器錯誤 C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 8b01a2f7b9c55fb57c880df5033538f4e45f76b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282322"
---
# <a name="compiler-error-c2410"></a>編譯器錯誤 C2410

'identifier': 'context' 中的模稜兩可的成員名稱

識別碼是一個以上的結構或等位在此內容中的成員。

使用造成錯誤的運算元是結構或等位的規範。 結構或等位的規範是識別項的型別`struct`或是`union`(`typedef`名稱或變數中的結構或等位正在參考相同的型別)。 規範必須是要使用運算元的第一個成員選取運算子 （.） 的左的運算元。