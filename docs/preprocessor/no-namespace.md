---
title: "no_namespace |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_namespace
dev_langs: C++
helpviewer_keywords: no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb41ec2820468180392a42e8f48684624c7d598d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)