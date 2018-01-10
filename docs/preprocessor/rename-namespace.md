---
title: "rename_namespace |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: rename_namespace
dev_langs: C++
helpviewer_keywords: rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 856762f9582f4a91275c29d49c5065e8436cc719
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)