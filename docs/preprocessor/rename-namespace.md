---
title: rename_namespace |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51114787dde2f858a8409538083282ef292d599
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="renamenamespace"></a>rename_namespace
**C + + 特定的**  
  
 將包含類型程式庫內容的命名空間重新命名。  
  
## <a name="syntax"></a>語法  
  
```  
rename_namespace("NewName")  
```  
  
#### <a name="parameters"></a>參數  
 `NewName`  
 命名空間的新名稱。  
  
## <a name="remarks"></a>備註  
 它會採用單一引數， *NewName*，指定命名空間的新名稱。  
  
 若要移除的命名空間，請使用[no_namespace](../preprocessor/no-namespace.md)屬性，屬性。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)