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
ms.openlocfilehash: f4acd81a5420f9fe2685e7570f26fea61691b845
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467400"
---
# <a name="using-atexit"></a>使用 atexit
具有[atexit](../c-runtime-library/reference/atexit.md)函式，您可以指定在程式結束之前執行的結束處理函式。 任何呼叫之前初始化的全域靜態物件**atexit**會終結之前執行結束處理函式。  
  
## <a name="see-also"></a>另請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)