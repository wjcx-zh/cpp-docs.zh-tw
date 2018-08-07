---
title: '運算子&lt;運算子 (microsoft:: wrl) |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
dev_langs:
- C++
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2de0d40a4b506da2cec36719b8fa2fe9c22108d8
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604209"
---
# <a name="operatorlt-operator-microsoftwrl"></a>運算子&lt;運算子 (microsoft:: wrl)
判斷一個物件的位址是否小於另一個。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template<class T, class U>  
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();  
template<class T, class U>  
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();  
```  
  
### <a name="parameters"></a>參數  
 *a*  
 左物件。  
  
 *b*  
 右物件。  
  
## <a name="return-value"></a>傳回值  
 **true**如果的地址小於的位址*b*; 否則**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)