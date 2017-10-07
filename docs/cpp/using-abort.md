---
title: "使用 abort |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 690e76eb3b83844e0fed81bf8d7bbd4c395abb14
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="using-abort"></a>使用 abort
呼叫[中止](../c-runtime-library/reference/abort.md)函式會導致立即終止。 它會略過初始化全域靜態物件的正常解構流程。 另外也會略過任何使用 `atexit` 函式指定的特殊處理。  
  
## <a name="see-also"></a>另請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)
