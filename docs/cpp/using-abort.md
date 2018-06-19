---
title: 使用 abort |Microsoft 文件
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
ms.openlocfilehash: 7231339ba4884445d7ad6b0161c6cff793c6db8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421844"
---
# <a name="using-abort"></a>使用 abort
呼叫[中止](../c-runtime-library/reference/abort.md)函式會導致立即終止。 它會略過初始化全域靜態物件的正常解構流程。 另外也會略過任何使用 `atexit` 函式指定的特殊處理。  
  
## <a name="see-also"></a>另請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)