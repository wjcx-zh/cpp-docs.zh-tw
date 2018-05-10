---
title: raw_method_prefix |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236c9042393e4ff3de57bea83ad566c8b74d5d3b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**C + + 特定的**  
  
 指定不同的前置詞，避免發生名稱衝突。  
  
## <a name="syntax"></a>語法  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>參數  
 `Prefix`  
 要使用的前置詞。  
  
## <a name="remarks"></a>備註  
 低層級的屬性和方法，由成員函式的前置詞**raw_** 以避免與高階錯誤處理成員函式的名稱衝突。  
  
> [!NOTE]
>  效果`raw_method_prefix`屬性將不會變更的存在[raw_interfaces_only](#_predir_raw_interfaces_only)屬性。 在指定前置詞時，`raw_method_prefix` 一定會優先於 `raw_interfaces_only`。 如果在相同的 `#import` 陳述式中使用了這兩個屬性，則會使用 `raw_method_prefix` 屬性指定的前置詞。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)