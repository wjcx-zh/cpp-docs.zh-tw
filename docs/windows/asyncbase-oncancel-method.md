---
title: 'Asyncbase:: Oncancel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::OnCancel
dev_langs:
- C++
helpviewer_keywords:
- OnCancel method
ms.assetid: 4bd0b68e-a9df-4913-9f6c-e093ed55c3f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b648718c715a43befbc5ead828c810dbfa92d120
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646870"
---
# <a name="asyncbaseoncancel-method"></a>AsyncBase::OnCancel 方法
當在衍生類別中覆寫時，取消非同步作業。  
  
## <a name="syntax"></a>語法  
  
```cpp  
virtual void OnCancel(  
   void  
) = 0;  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)   
 [AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)