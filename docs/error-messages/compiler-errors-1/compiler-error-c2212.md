---
title: 編譯器錯誤 C2212 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2212
dev_langs:
- C++
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 773dff4c731830d300c97f1960b24923d2b7d67f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089875"
---
# <a name="compiler-error-c2212"></a>編譯器錯誤 C2212

'identifier': __based 不提供函式指標

函式的指標不可以宣告為`__based`。 如果您需要的程式碼為基礎的資料，請使用`__declspec`關鍵字或`data_seg`pragma。