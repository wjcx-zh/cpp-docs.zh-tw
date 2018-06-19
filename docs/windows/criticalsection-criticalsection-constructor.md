---
title: 'Criticalsection:: Criticalsection 建構函式 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d86c80d169cb6d9794f163290c30bf1b2563588b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870893"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection 建構函式
初始化同步處理物件類似於 mutex 物件，但可用來在單一處理序執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### <a name="parameters"></a>參數  
 `spincount`  
 微調關鍵區段物件計數。 預設值為 0。  
  
## <a name="remarks"></a>備註  
 多個關鍵區段和 spincounts 的詳細資訊，請參閱**InitializeCriticalSectionAndSpinCount** Windows API 文件的同步處理區段中的函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)
