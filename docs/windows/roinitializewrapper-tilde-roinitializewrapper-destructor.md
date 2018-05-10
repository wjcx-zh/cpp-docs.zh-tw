---
title: 'RoInitializeWrapper:: ~ RoInitializeWrapper 解構函式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
ms.assetid: afef4c1f-ffde-4cd2-8654-8de4182eb5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29683e68f1f5aadcd477cdc717b03a648c5cccc7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="roinitializewrapperroinitializewrapper-destructor"></a>RoInitializeWrapper::~RoInitializeWrapper 解構函式
未初始化 Windows 執行階段。  
  
## <a name="syntax"></a>語法  
  
```cpp  
~RoInitializeWrapper()  
```  
  
## <a name="remarks"></a>備註  
 RoInitializeWrapper 類別叫用 Windows::Foundation::Uninitialize()。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)