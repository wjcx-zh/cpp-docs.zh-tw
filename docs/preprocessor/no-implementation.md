---
title: "no_implementation |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_implementation
dev_langs: C++
helpviewer_keywords: no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0a8337de519b2b0d43e8d5035e3845e1aefbe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="noimplementation"></a>no_implementation
**C + + 特定的**  
  
 不產生 .tli 標頭，其中包含包裝函式成員函式的實作。  
  
## <a name="syntax"></a>語法  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>備註  
 如果已指定這個屬性，則會產生 .tlh 標頭 (具有公開類型程式庫項目的宣告)，但沒有 `#include` 陳述式可包含 .tli 標頭檔。  
  
 這個屬性用於搭配[implementation_only](../preprocessor/implementation-only.md)。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)