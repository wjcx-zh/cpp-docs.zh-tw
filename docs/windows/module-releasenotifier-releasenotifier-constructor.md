---
title: Module::ReleaseNotifier::ReleaseNotifier 建構函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93dca0500971f0bcfdefd017457e02bf6a033660
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608465"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier 建構函式
初始化的新執行個體**releasenotifier**類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
### <a name="parameters"></a>參數  
 *release*  
 **真**若要刪除這個執行個體時`Release`方法稱為;**false**未刪除此執行個體。  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)