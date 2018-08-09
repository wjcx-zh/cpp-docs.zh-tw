---
title: 'Asyncbase:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ce391e95aa9e08ae7d99e3cbdf064721ce21dbe
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643533"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close 方法
關閉的非同步作業。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果作業會關閉或已關閉否則，E_ILLEGAL_STATE_CHANGE。  
  
## <a name="remarks"></a>備註  
 **Close （)** 的預設實作`IAsyncInfo::Close`，並不執行任何實際工作。 若要實際關閉非同步作業，請覆寫`OnClose()`純虛擬方法。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)