---
title: no_implementation |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf756a411404d2ebb821d5b226818844acfca75b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
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
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)