---
title: 'Module:: unregisterobjects 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c46fad71a42f9f947f020709cdf7851d079edd81
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014022"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects 方法
取消註冊指定的模組中的物件，以便讓其他應用程式無法連線。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
### <a name="parameters"></a>參數  
 *模組*  
 模組的指標。  
  
 *伺服器名稱*  
 合格的名稱，指定此作業所影響的物件子集。  
  
## <a name="return-value"></a>傳回值  
 如果這項作業是成功則為 S_OK否則為錯誤的 HRESULT 指出的原因，這項作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)