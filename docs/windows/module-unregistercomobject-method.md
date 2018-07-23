---
title: 'Module:: unregistercomobject 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de4cc44d88f59e18f2c1644e9b27a9214ad32962
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881932"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject 方法
取消註冊一或多個 COM 物件，如此可防止其他應用程式無法連線到它們。  
  
## <a name="syntax"></a>語法  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
#### <a name="parameters"></a>參數  
 `serverName`  
 （未使用）  
  
 `cookies`  
 識別要移除註冊類別物件的值的指標陣列。 陣列由[RegisterCOMObject](../windows/module-registercomobject-method.md)方法。  
  
 `count`  
 若要取消註冊的類別數目。  
  
## <a name="return-value"></a>傳回值  
 如果此作業成功，為 S_OK否則，指出的原因的 HRESULT 錯誤的作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)