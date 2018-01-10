---
title: "Module:: registerobjects 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::RegisterObjects
dev_langs: C++
helpviewer_keywords: RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e73a59ff18c16a898ca1a9d7919615a2dec18bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
 
## <a name="see-also"></a>請參閱
[Module 類別](../windows/module-class.md)