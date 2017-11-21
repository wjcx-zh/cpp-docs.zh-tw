---
title: "Criticalsection:: Criticalsection 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs: C++
helpviewer_keywords: CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bf4e9cd4d4fde31f1809e7d583e662188558d5b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
 Crticial 各區段及 spincounts 相關的詳細資訊，請參閱**InitializeCriticalSectionAndSpinCount** Windows API 文件的同步處理區段中的函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)