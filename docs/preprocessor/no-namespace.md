---
title: no_namespace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e6528ce33689dc05fa037bdd6bc110e5e6a0de9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="nonamespace"></a>no_namespace
**C + + 特定的**  
  
 指定命名空間名稱不是由編譯器產生。  
  
## <a name="syntax"></a>語法  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>備註  
 `#import` 標頭檔中的類型程式庫內容通常是在命名空間中定義。 命名空間名稱已在指定**文件庫**陳述式的原始 IDL 檔案。 如果指定了 `no_namespace` 屬性，則此命名空間名稱不是由編譯器產生。  
  
 如果您想要使用不同的命名空間名稱，然後使用[rename_namespace](../preprocessor/rename-namespace.md)屬性，屬性。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)