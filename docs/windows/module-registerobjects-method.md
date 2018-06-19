---
title: 'Module:: registerobjects 方法 |Microsoft 文件'
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
ms.openlocfilehash: 986dcfff49529eedd8d495f4c37e19fa2b6cb8bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875340"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects 方法
註冊 COM 或 Windows 執行階段物件，讓其他應用程式可以連接到它們。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>參數  
 `module`  
 COM 或 Windows 執行階段物件的陣列。  
  
 `serverName`  
 建立物件的伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，表示原因作業失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
## <a name="see-also"></a>另請參閱
[Module 類別](../windows/module-class.md)