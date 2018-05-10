---
title: HStringReference 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90e94471fe114eafec91a19ddad5d47ce39a8de7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="hstringreference-class"></a>HStringReference 類別
代表 HSTRING 建立從現有的字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>備註  
 在新 HSTRING 備份緩衝區存留期不是由 Windows 執行階段管理。 呼叫端配置來源字串上的堆疊框架，以避免堆積配置，並排除記憶體流失的風險。 此外，呼叫端必須確保附加 HSTRING 存留期間，來源字串維持不變。 如需詳細資訊，請參閱[WindowsCreateStringReference 函式](http://msdn.microsoft.com/en-us/0361bb7e-da49-4289-a93e-de7aab8712ac)。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[HStringReference::HStringReference 建構函式](../windows/hstringreference-hstringreference-constructor.md)|初始化 HStringReference 類別的新執行個體。|  
  
### <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|[HStringReference::CopyTo 方法](../windows/hstringreference-copyto-method.md)|複製目前 HStringReference HSTRING 物件的物件。|  
|[HStringReference::Get 方法](../windows/hstringreference-get-method.md)|擷取基礎 HSTRING 控制代碼的值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[HStringReference::Operator= 運算子](../windows/hstringreference-operator-assign-operator.md)|將另一個 HStringReference 物件的值移至目前 HStringReference 物件。|  
|[HStringReference::Operator== 運算子](../windows/hstringreference-operator-equality-operator.md)|指出兩個參數是否相等。|  
|[HStringReference::Operator!= 運算子](../windows/hstringreference-operator-inequality-operator.md)|指出兩個參數是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `HStringReference`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)