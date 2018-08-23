---
title: tlbid |Microsoft Docs
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
ms.openlocfilehash: 1ec0150e63209728cf2f02c854fe03702b8a45b4
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541372"
---
# <a name="tlbid"></a>tlbid
**C + + 特定**  
  
允許載入主要類型程式庫以外的程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
tlbid(number)  
```  
  
### <a name="parameters"></a>參數  
*數字*  
`filename` 中類型程式庫的號碼。  
  
## <a name="remarks"></a>備註  
 
如果多個型別程式庫會建置成單一 DLL，您可以使用載入主要類型程式庫以外的程式庫**tlbid**。  
  
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