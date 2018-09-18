---
title: 使用 atexit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d5164394853d2ac4f18efc94863b8fc3fa5ba78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053124"
---
# <a name="using-atexit"></a>使用 atexit

具有[atexit](../c-runtime-library/reference/atexit.md)函式，您可以指定在程式結束之前執行的結束處理函式。 任何呼叫之前初始化的全域靜態物件**atexit**會終結之前執行結束處理函式。

## <a name="see-also"></a>另請參閱

[其他終止考量](../cpp/additional-termination-considerations.md)