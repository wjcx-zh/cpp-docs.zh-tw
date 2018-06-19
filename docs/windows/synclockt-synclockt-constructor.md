---
title: 'Synclockt:: Synclockt 建構函式 |Microsoft 文件'
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
ms.openlocfilehash: c3353df1a73821a2009aeba2367f1892b06aba5b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889834"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT 建構函式
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
#### <a name="parameters"></a>參數  
 `other`  
 右值參考到另一個 SyncLockT 物件。  
  
 `sync`  
 另一個 SyncLockWithStatusT 物件的參考。  
  
## <a name="remarks"></a>備註  
 初始化 SyncLockT 類別的新執行個體。  
  
 第一個建構函式會初始化參數所指定的另一個 SyncLockT 物件從目前的 SyncLockT 物件`other`，然後則 SyncLockT 物件。 第二個建構函式是`protected`，並將目前 SyncLockT 物件初始化為無效的狀態。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)