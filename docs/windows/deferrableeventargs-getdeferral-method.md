---
title: "Deferrableeventargs:: Getdeferral 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d43aa6d82f44965e8defda2af3e6455e86cba38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral 方法
取得參考[延期](http://go.microsoft.com/fwlink/?LinkId=526520)物件代表延期的事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>參數  
 `result`  
 將參考的指標[延期](http://go.microsoft.com/fwlink/?LinkId=526520)物件呼叫完成時。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="remarks"></a>備註  
 如需程式碼範例，請參閱[DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)