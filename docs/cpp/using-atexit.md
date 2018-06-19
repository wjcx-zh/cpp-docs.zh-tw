---
title: 使用 atexit |Microsoft 文件
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
ms.openlocfilehash: 1bb0c89c34b5107326a961e874289d20cbd2385c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420963"
---
# <a name="using-atexit"></a>使用 atexit
與[atexit](../c-runtime-library/reference/atexit.md)函式，您可以指定在程式結束之前執行結束處理函式。 執行結束處理函式之前，不會終結在呼叫 `atexit` 之前初始化的全域靜態物件。  
  
## <a name="see-also"></a>另請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)