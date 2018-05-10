---
title: 'Hstringreference:: Hstringreference 建構函式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc88ea32d4384b36559a4a10da0a5975345bf0d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference 建構函式
初始化 HStringReference 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `sizeDest`  
 樣板參數，指定目的地 HStringReference 緩衝區的大小。  
  
 `str`  
 寬字元字串的參考。  
  
 `len`  
 最大長度`str`来使用這項作業中的參數緩衝區。 如果`len`參數未指定，整個`str`使用參數。 如果`len`大於`sizeDest`，`len`設`sizeDest`-1。  
  
 `other`  
 另一個 HStringReference 物件。  
  
## <a name="remarks"></a>備註  
 第一個建構函式會初始化參數大小相同的新 HStringReference 物件`str`。  
  
 第二個建構函式初始化新 HStringReference 物件參數大小 specifeid `len`。  
  
 第三個建構函式會初始化新 HStringReference 物件的值`other`參數，再終結`other`參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)