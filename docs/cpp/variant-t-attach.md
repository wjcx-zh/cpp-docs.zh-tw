---
title: _variant_t::Attach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42c275d085434cc8077a0629429c7c0e1cbbfcc3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942977"
---
# <a name="varianttattach"></a>_variant_t::Attach
**Microsoft 專屬**  
  
 附加`VARIANT`物件插入`_variant_t`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
void Attach(VARIANT& varSrc);  
```  
  
#### <a name="parameters"></a>參數  
 *varSrc*  
 A`VARIANT`要附加至此物件`_variant_t`物件。  
  
## <a name="remarks"></a>備註  
 取得擁有權的`VARIANT`透過封裝方式。 此成員函式會釋放所有現有的封裝`VARIANT`，然後複製提供`VARIANT`，並設定其`VARTYPE`設為 VT_EMPTY 以確定其可以只會釋放資源`_variant_t`解構函式。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)