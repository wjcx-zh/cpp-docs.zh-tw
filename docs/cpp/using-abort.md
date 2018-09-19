---
title: 使用 abort |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3edc24b2b8dc869022039d4aaaea73af06eac16b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092522"
---
# <a name="using-abort"></a>使用 abort

呼叫[中止](../c-runtime-library/reference/abort.md)函式會導致立即終止。 它會略過初始化全域靜態物件的正常解構流程。 另外也會略過任何使用 `atexit` 函式指定的特殊處理。

## <a name="see-also"></a>另請參閱

[其他終止考量](../cpp/additional-termination-considerations.md)