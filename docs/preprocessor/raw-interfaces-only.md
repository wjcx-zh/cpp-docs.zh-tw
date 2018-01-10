---
title: "raw_interfaces_only |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_interfaces_only
dev_langs: C++
helpviewer_keywords: raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d7790601a3eec16cae67542ac2d8d622b71df2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C + + 特定的**  
  
 隱藏的錯誤處理的包裝函式產生和[屬性](../cpp/property-cpp.md)使用這些包裝函式的宣告。  
  
## <a name="syntax"></a>語法  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>備註  
 `raw_interfaces_only` 屬性 (Attribute) 也會造成用於命名非屬性 (Property) 函式的預設前置詞遭到移除。 一般來說，前置詞是**raw_**。 如果指定這個屬性，函式名稱會直接來自類型程式庫。  
  
 這個屬性只能讓您公開類型程式庫中的低階內容。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)