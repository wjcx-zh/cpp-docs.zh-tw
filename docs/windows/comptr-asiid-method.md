---
title: "Comptr:: Asiid 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::AsIID
dev_langs: C++
helpviewer_keywords: AsIID method
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e19a313da257d9aefce68a61d43278e22bf88bab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptrasiid-method"></a>ComPtr::AsIID 方法
傳回 ComPtr 物件，代表指定介面 ID 所識別的介面。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IUnknown>* p  
) const;  
```  
  
#### <a name="parameters"></a>參數  
 `riid`  
 介面識別碼。  
  
 `p`  
 如果支援，指定的介面的雙向間接指標`riid`參數，否則 IUnknown 的指標。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [ComPtr 類別](../windows/comptr-class.md)