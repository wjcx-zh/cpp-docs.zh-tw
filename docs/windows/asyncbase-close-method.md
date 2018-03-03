---
title: "Asyncbase:: Close 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35b7fda0ab10ff80df0f4a27f6e79028e73574fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close 方法
關閉的非同步作業。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果作業會關閉或已關閉。否則，E_ILLEGAL_STATE_CHANGE。  
  
## <a name="remarks"></a>備註  
 Close （） 是 IAsyncInfo::Close 的預設實作，而且不執行任何實際工作。 若要實際關閉非同步作業，覆寫 onclose （） 之中的純虛擬方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)