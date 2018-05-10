---
title: tlbid |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d651546733f42b1a714ac7a39992fa2d392c8fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="tlbid"></a>tlbid
**C + + 特定的**  
  
 允許載入主要類型程式庫以外的程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
tlbid(number)  
```  
  
#### <a name="parameters"></a>參數  
 `number`  
 `filename` 中類型程式庫的號碼。  
  
## <a name="remarks"></a>備註  
 如果有多個類型程式庫內建於單一 DLL 中，它可能會使用 `tlbid` 載入主要類型程式庫以外的程式庫。  
  
 例如:   
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 等於：  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)