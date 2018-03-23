---
title: 'Module:: create 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e566b34140c0b82072c8469cd8d965f807e244ec
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="modulecreate-method"></a>Module::Create 方法
建立模組的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW static Module& Create();  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 模組類型。  
  
 `callback`  
 當您釋放最後一個執行個體物件的模組時呼叫。  
  
 `object`  
 `object`和`method`搭配使用的參數。 點的最後一個執行個體物件時釋放模組中的最後一個執行個體物件。  
  
 `method`  
 `object`和`method`搭配使用的參數。 指向方法時釋放最後一個執行個體物件模組中的最後一個執行個體物件。  
  
## <a name="return-value"></a>傳回值  
 此模組參考。  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
[Module 類別](../windows/module-class.md)

 