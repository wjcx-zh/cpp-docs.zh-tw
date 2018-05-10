---
title: CloakedIid 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
dev_langs:
- C++
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57ad76b48b92519eaeed089dfb14817c38273588
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="cloakediid-structure"></a>CloakedIid 結構
指出 RuntimeClass、Implements 和 ChainInterfaces 範本指定介面無法在 IID 清單中存取。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename T>  
struct CloakedIid : T;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 介面隱藏的 （隱匿）。  
  
## <a name="remarks"></a>備註  
 下列是如何使用 CloakedIid 的範例： `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `T`  
  
 `CloakedIid`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)