---
title: "Synclockwithstatust:: Synclockwithstatust 建構函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc5be4a37182cb23b47a2511d2e7d5eb0ffa558a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT 建構函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### <a name="parameters"></a>參數  
 `other`  
 右值參考到另一個 SyncLockWithStatusT 物件。  
  
 `sync`  
 另一個 SyncLockWithStatusT 物件的參考。  
  
 `status`  
 值[status_](../windows/synclockwithstatust-status-data-member.md)資料成員`other`參數或`sync`參數。  
  
## <a name="remarks"></a>備註  
 初始化 SyncLockWithStatusT 類別的新執行個體。  
  
 第一個建構函式初始化目前 SyncLockWithStatusT 物件從另一個參數所指定的 SyncLockWithStatusT `other`，然後則 SyncLockWithStatusT 物件。 第二個建構函式是`protected`，並將目前 SyncLockWithStatusT 物件初始化為無效的狀態。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>請參閱  
 [SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)