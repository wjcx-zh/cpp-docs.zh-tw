---
title: 'Comptr:: Attach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78b5039268bd122ade815ed6040a1df546e0f293
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641326"
---
# <a name="comptrattach-method"></a>ComPtr::Attach 方法
將這**ComPtr**與目前的範本類型參數所指定的介面類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
### <a name="parameters"></a>參數  
 *other*  
 介面型別。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)