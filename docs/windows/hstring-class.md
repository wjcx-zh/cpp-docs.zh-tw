---
title: "HString 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e8d66f134eef5f2ecb75b30fd68874418dbc49d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hstring-class"></a>HString 類別
HSTRING 使用 RAII 模式的存留期的協助程式類別。
  
## <a name="syntax"></a>語法  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>備註  
 Windows 執行階段存取透過 HSTRING 控制代碼的字串。 HString 類別提供方便函式和運算子，以簡化使用 HSTRING 控制代碼。 這個類別可以處理其擁有 RAII 模式透過 HSTRING 的存留期。 
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[HString::HString 建構函式](../windows/hstring-hstring-constructor.md)|初始化 HString 類別的新執行個體。|  
|[HString::~HString 解構函式](../windows/hstring-tilde-hstring-destructor.md)|終結 HString 類別的目前執行個體。|  
  
### <a name="members"></a>成員  
  
|名稱|描述|  
|----------|-----------------|  
|[HString::Set 方法](../windows/hstring-set-method.md)|將目前 HString 物件的值設為指定的寬字元字串或 HString 參數。|  
|[HString::Attach 方法](../windows/hstring-attach-method.md)|將指定的 HString 物件與目前 HString 物件產生關聯。|  
|[HString::CopyTo 方法](../windows/hstring-copyto-method.md)|複製目前 HString HSTRING 物件的物件。|  
|[HString::Detach 方法](../windows/hstring-detach-method.md)|解除指定的 HString 物件從其基礎值的關聯。|  
|[HString::GetAddressOf 方法](../windows/hstring-getaddressof-method.md)|擷取基礎 HSTRING 控制代碼的指標。|  
|[HString::Get 方法](../windows/hstring-get-method.md)|擷取基礎 HSTRING 控制代碼的值。|  
|[HString::Release 方法](../windows/hstring-release-method.md)|刪除的基礎字串值，並初始化為空值的目前 HString 物件。|  
|[HString::MakeReference 方法](../windows/hstring-makereference-method.md)|從指定的字串參數建立 HStringReference 物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[HString::Operator= 運算子](../windows/hstring-operator-assign-operator.md)|將另一個 HString 物件的值移至目前 HString 物件。|  
|[HString::Operator== 運算子](../windows/hstring-operator-equality-operator.md)|指出兩個參數是否相等。|  
|[HString::Operator!= 運算子](../windows/hstring-operator-inequality-operator.md)|指出兩個參數是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `HString`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)