---
title: "_variant_t::ChangeType |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs: C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8fea359c3f256d56f4d112fe93bb736a16892ea4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Microsoft 特定的**  
  
 類型變更`_variant_t`物件指定**VARTYPE**。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>參數  
 `vartype`  
 **VARTYPE**這個`_variant_t`物件。  
  
 `pSrc`  
 要轉換之 `_variant_t` 物件的指標。 如果此值為**NULL**，備妥進行轉換。  
  
## <a name="remarks"></a>備註  
 此成員函式會將轉換`_variant_t`為指定的物件**VARTYPE**。 如果`pSrc`是**NULL**，表示轉換已完成的位置，否則這`_variant_t`物件從複製`pSrc`，然後再轉換。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)