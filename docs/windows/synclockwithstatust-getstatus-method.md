---
title: 'Synclockwithstatust:: Getstatus 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 03addd8d89c54eddb5deb721ab47d46e8b945edd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889758"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus 方法
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>傳回值  
 以類別為基礎 SyncLockWithStatusT，例如在物件上的等候作業的結果[Mutex](../windows/mutex-class1.md)或[號誌](../windows/semaphore-class.md)。 零 (0) 表示等待作業傳回信號的狀態。否則，另一個狀態發生，例如經過逾時值。  
  
## <a name="remarks"></a>備註  
 擷取目前 SyncLockWithStatusT 物件的等候狀態。  
  
 GetStatus() 函式擷取的基礎值[status_](../windows/synclockwithstatust-status-data-member.md)資料成員。 SyncLockWithStatusT 類別為基礎的物件執行鎖定作業時，當物件第一次等候物件可以使用。 等候作業的結果會儲存在`status_`資料成員。 可能值`status_`資料成員會等候作業的傳回值。 如需詳細資訊，請參閱的傳回值**WaitForSingleObjectEx()** MSDN Library 中的函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)