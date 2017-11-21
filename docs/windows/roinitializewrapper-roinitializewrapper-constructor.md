---
title: "Roinitializewrapper:: Roinitializewrapper 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs: C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88ef0885c49ba7ba28afe40aea25a74eb55d46e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper 建構函式
初始化 RoInitializeWrapper 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```  
  
#### <a name="parameters"></a>參數  
 `flags`  
 其中一個指定的 Windows 執行階段所提供的支援 RO_INIT_TYPE 列舉型別。  
  
## <a name="remarks"></a>備註  
 RoInitializeWrapper 類別叫用 Windows::Foundation::Initialize (*旗標*)。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)