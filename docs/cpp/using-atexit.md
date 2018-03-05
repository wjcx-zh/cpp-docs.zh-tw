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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7aec0e5aedb2d17e7d22b4f480eaef2be26413fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-atexit"></a>使用 atexit
與[atexit](../c-runtime-library/reference/atexit.md)函式，您可以指定在程式結束之前執行結束處理函式。 執行結束處理函式之前，不會終結在呼叫 `atexit` 之前初始化的全域靜態物件。  
  
## <a name="see-also"></a>請參閱  
 [其他終止考量](../cpp/additional-termination-considerations.md)