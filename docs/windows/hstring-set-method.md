---
title: 'Hstring:: Set 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
dev_langs:
- C++
ms.assetid: c9b3d613-95c4-48b0-999d-f5baf0804faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18ea9eafe3786d0a0df543cde654e1f0270dc8c7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011763"
---
# <a name="hstringset-method"></a>HString::Set 方法
設定目前的值**HString**設為指定的寬字元字串的物件或**HString**參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Set(  
          const wchar_t* str) throw();  
HRESULT Set(   
          const wchar_t* str,   
          unsigned int len  
           ) throw();  
HRESULT Set(  
          const HSTRING& hstr  
           ) throw();  
```  
  
### <a name="parameters"></a>參數  
 *str*  
 寬字元字串。  
  
 *Len*  
 最大長度*str*指派給目前的參數**HString**物件。  
  
 *hstr*  
 將現有**HString**物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)