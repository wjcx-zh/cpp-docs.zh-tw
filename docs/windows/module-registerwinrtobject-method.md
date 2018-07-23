---
title: 'Module:: registerwinrtobject 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 097bf70ebd280d9494ff70ea1d80f53615f3d898
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874950"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject 方法
註冊一個或多個 Windows 執行階段物件，讓其他應用程式可以連接到它們。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>參數  
 `serverName`  
 指定此作業所影響的物件子集的名稱。  
  
 `activatableClassIds`  
 若要註冊的可啟動 Clsid 的陣列。  
  
 `cookie`  
 識別已註冊類別物件的值。 若要撤銷註冊稍後會使用此值。  
  
 `count`  
 若要註冊的物件數目。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，例如 CO_E_OBJISREG 表示原因的 HRESULT 錯誤的作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)