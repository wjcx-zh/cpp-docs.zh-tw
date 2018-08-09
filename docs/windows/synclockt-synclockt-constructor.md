---
title: 'Synclockt:: Synclockt 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceaafd6230e6497ed2b7636ad5070141546cb8d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648161"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT 建構函式
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
### <a name="parameters"></a>參數  
 *other*  
 右值參考到另一個**SyncLockT**物件。  
  
 *sync*  
 另一個的參考`SyncLockWithStatusT`物件。  
  
## <a name="remarks"></a>備註  
 初始化的新執行個體**SyncLockT**類別。  
  
 第一個建構函式初始化目前**SyncLockT**物件從另一個**SyncLockT**參數所指定的物件*其他*，接著則其他**SyncLockT**物件。 第二個建構函式**保護**，並初始化目前**SyncLockT**為無效狀態的物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)