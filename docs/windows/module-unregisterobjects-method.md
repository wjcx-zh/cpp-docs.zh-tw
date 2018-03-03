---
title: "Module:: unregisterobjects 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d7e55afb96805fba6558cb900d2421a86379791c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects 方法
取消註冊指定的模組中的物件，以便讓其他應用程式無法連線。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>參數  
 `module`  
 模組的指標。  
  
 `serverName`  
 合格的名稱，指定此作業所影響的物件子集。  
  
## <a name="return-value"></a>傳回值  
 如果此作業成功，為 S_OK否則，錯誤指出的原因的 HRESULT 這項作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>請參閱
 [Module 類別](../windows/module-class.md)