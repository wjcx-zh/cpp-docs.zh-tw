---
title: 'Module:: create 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99ede64c239909956f1f767db34a2a6a14c02314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874885"
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

 