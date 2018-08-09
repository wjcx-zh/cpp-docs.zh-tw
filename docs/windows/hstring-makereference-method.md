---
title: 'Hstring:: Makereference 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c9a77a8a943dcefdf9db9d43121f2b00bde1568
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011006"
---
# <a name="hstringmakereference-method"></a>HString::MakeReference 方法
建立`HStringReference`從指定的字串參數的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
### <a name="parameters"></a>參數  
 *sizeDest*  
 樣板參數，指定大小的目的地`HStringReference`緩衝區。  
  
 *str*  
 寬字元字串的參考。  
  
 *Len*  
 最大長度*str*来使用這項作業中的參數緩衝區。 如果*len*參數未指定，整個*str*參數使用。  
  
## <a name="return-value"></a>傳回值  
 `HStringReference`物件，其值為與指定相同*str*參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)