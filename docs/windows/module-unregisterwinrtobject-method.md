---
title: "Module:: unregisterwinrtobject 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs: C++
helpviewer_keywords: UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1c5f1fe4da0d9c0699ab7205ad7823ca8d506dd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject 方法
取消註冊一或多個 Windows 執行階段物件，以便讓其他應用程式無法連線。  
  
## <a name="syntax"></a>語法  
  
```  
virtual HRESULT UnregisterWinRTObject(  
   unsigned int,  
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `cookie`  
 值，識別要撤銷其註冊的類別物件指標。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [Module 類別](../windows/module-class.md)