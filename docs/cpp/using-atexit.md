---
title: "使用 atexit |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4093bf14422fb6598f53d298aa8958a506103fb2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="using-atexit"></a>使用 atexit
與[atexit](../c-runtime-library/reference/atexit.md)函式，您可以指定在程式結束之前執行結束處理函式。 執行結束處理函式之前，不會終結在呼叫 `atexit` 之前初始化的全域靜態物件。  
  
## <a name="see-also"></a>另請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)
