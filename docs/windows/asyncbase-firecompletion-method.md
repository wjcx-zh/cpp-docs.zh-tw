---
title: "Asyncbase:: Firecompletion 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::FireCompletion
dev_langs: C++
helpviewer_keywords: FireCompletion method
ms.assetid: b5e29d6d-52e7-4148-a7f3-a313b1359819
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f5478b7ea3777230eb4adcb9f94cd15cbb9cd9d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasefirecompletion-method"></a>AsyncBase::FireCompletion 方法
完成事件處理常式，會叫用，或重設內部進行委派。  
  
## <a name="syntax"></a>語法  
  
```  
void FireCompletion(  
   void  
) override;  
  
virtual void FireCompletion();  
```  
  
## <a name="remarks"></a>備註  
 FireCompletion() 的第一個版本會重設內部進行委派變數。 如果非同步作業已完成，則第二個版本會叫用完成事件處理常式。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)