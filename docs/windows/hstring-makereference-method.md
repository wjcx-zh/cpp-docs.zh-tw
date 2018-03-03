---
title: "Hstring:: Makereference 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e2eba5756f2c18830c4c8fe7e16f2751ea61ac1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hstringmakereference-method"></a>HString::MakeReference 方法
從指定的字串參數建立 HStringReference 物件。  
  
## <a name="syntax"></a>語法  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
#### <a name="parameters"></a>參數  
 `sizeDest`  
 樣板參數，指定目的地 HStringReference 緩衝區的大小。  
  
 `str`  
 寬字元字串的參考。  
  
 `len`  
 最大長度`str`来使用這項作業中的參數緩衝區。 如果`len`參數未指定，整個`str`使用參數。  
  
## <a name="return-value"></a>傳回值  
 HStringReference 物件，其值為與指定的相同`str`參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [HString 類別](../windows/hstring-class.md)