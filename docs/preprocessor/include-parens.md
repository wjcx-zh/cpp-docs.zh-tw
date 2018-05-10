---
title: include （) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 756aea4400d98b2bf061a54955b3df4b4eddd993
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="include"></a>include()
**C + + 特定的**  
  
 停用自動排除。  
  
## <a name="syntax"></a>語法  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>參數  
 `Name1`  
 要強制包含的第一個項目。  
  
 `Name2`  
 要強制包含的第二個項目 (如果需要的話)。  
  
## <a name="remarks"></a>備註  
 類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。 如果項目已排除，由[編譯器警告 （層級 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)，而且它們不能有已，這個屬性可以用來停用自動排除。 這個屬性可以接受任意數目的引數，每個引數都會是要包含的類型程式庫項目名稱。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)