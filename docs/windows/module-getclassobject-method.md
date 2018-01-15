---
title: "Module:: getclassobject 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GetClassObject
dev_langs: C++
helpviewer_keywords: GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f234b46da1a70ee0256a9a38ebb2ef7ae0bb5bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject 方法
擷取快取的 class factory。  
  
## <a name="syntax"></a>語法  
  
```  
 HRESULT GetClassObject(  
   REFCLSID clsid,  
   REFIID riid,  
   _Deref_out_ void **ppv,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `clsid`  
 類別識別碼。  
  
 `riid`  
 您要求的介面 ID。  
  
 `ppv`  
 傳回的物件指標。  
  
 `serverName`  
 在指定的伺服器名稱`ActivatableClassWithFactory`， `ActivatableClassWithFactoryEx`，或`ActivatableClass`巨集; 或`nullptr`取得預設的伺服器名稱。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 這個方法只能用於 COM，不使用 Windows 執行階段。 這個方法會公開只有 IClassFactory 方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>請參閱
 [Module 類別](../windows/module-class.md)