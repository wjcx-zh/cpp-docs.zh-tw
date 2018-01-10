---
title: "排除 (#import) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exclude
dev_langs: C++
helpviewer_keywords: exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd63eed4eea9404fd0a542c0be20f1770e461508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exclude-import"></a>exclude (#import)
**C + + 特定的**  
  
 排除從類型程式庫標頭檔產生的項目。  
  
## <a name="syntax"></a>語法  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### <a name="parameters"></a>參數  
 `Name1`  
 要排除的第一個項目。  
  
 `Name2`  
 要排除的第二個項目 (如果需要的話)。  
  
## <a name="remarks"></a>備註  
 類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 這個屬性可以接受任意數目的引數，每一個都是要排除的頂層類型程式庫項目。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)