---
title: ImplementsHelper 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58f27e418946987633f771bc8d2c3224bc2cd7fd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875935"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 結構
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>參數  
 `RuntimeClassFlagsT`  
 指定一或多個旗標欄位[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。  
  
 `ILst`  
 介面 Id 的清單。  
  
 `IsDelegateToClass`  
 指定`true`中的第一個介面 ID 的基底類別實作的目前執行個體是否`ILst`，否則`false`。  
  
## <a name="remarks"></a>備註  
 可協助實作[實作](../windows/implements-structure.md)結構。  
  
 此範本會周遊的介面清單，並將它們加入做為基底類別，以及啟用 QueryInterface 所需的資訊。  
  
## <a name="members"></a>成員  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ImplementsHelper`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [參考 （Windows 執行階段程式庫）](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)