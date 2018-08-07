---
title: 'Module:: registerobjects 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterObjects
dev_langs:
- C++
helpviewer_keywords:
- RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bdaa1b23bbefb64071e5f1f330c8708f9f9516ad
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605262"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects 方法
註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連線到它們。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
### <a name="parameters"></a>參數  
 *模組*  
 COM 或 Windows 執行階段物件的陣列。  
  
 *伺服器名稱*  
 建立物件的伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功則為 S_OK否則，HRESULT，指出的原因，作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
## <a name="see-also"></a>另請參閱
[Module 類別](../windows/module-class.md)