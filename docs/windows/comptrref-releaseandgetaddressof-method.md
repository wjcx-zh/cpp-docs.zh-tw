---
title: "Comptrref:: Releaseandgetaddressof 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
dev_langs: C++
helpviewer_keywords: ReleaseAndGetAddressOf method
ms.assetid: 004aac42-e135-41ce-8d1d-4c5969d55004
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 216e1b5e2a9343e780858c0f19578d970cead593
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="comptrrefreleaseandgetaddressof-method"></a>ComPtrRef::ReleaseAndGetAddressOf 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
InterfaceType** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>傳回值  
 已刪除的 ComPtrRef 物件所代表的介面指標。  
  
## <a name="remarks"></a>備註  
 刪除目前的 ComPtrRef 物件，並傳回已 ComPtrRef 物件所代表的介面指標至 a 的指標。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [ComPtrRef 類別](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)