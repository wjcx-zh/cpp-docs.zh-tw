---
title: 使用 abort
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: db0f6cdcdaf4bca1b74d89a9415c4f7951455d80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187853"
---
# <a name="using-abort"></a>使用 abort

呼叫[abort](../c-runtime-library/reference/abort.md)函式會導致立即終止。 它會略過初始化全域靜態物件的正常解構流程。 另外也會略過任何使用 `atexit` 函式指定的特殊處理。

## <a name="see-also"></a>另請參閱

[其他終止考量](../cpp/additional-termination-considerations.md)
