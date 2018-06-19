---
title: raw_interfaces_only |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4643181bf70bc92f4ef5e88b8a9add1ba7bdaad7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849297"
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
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)