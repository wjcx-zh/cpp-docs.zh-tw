---
title: 'Synclockwithstatust:: Getstatus 方法 |Microsoft Docs'
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
ms.openlocfilehash: 4677239bbcaff0c72eb11ade259f47531a616f19
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649632"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>傳回值  
 以物件為基礎的等候作業的結果**SyncLockWithStatusT**類別，例如[Mutex](../windows/mutex-class1.md)或是[號誌](../windows/semaphore-class.md)。 零 (0) 表示等待作業傳回信號的狀態;否則，另一個狀態發生，例如逾時值過。  
  
## <a name="remarks"></a>備註  
 擷取目前的等候狀態**SyncLockWithStatusT**物件。  
  
 GetStatus() 函式擷取值的基礎[status_](../windows/synclockwithstatust-status-data-member.md)資料成員。 當物件為基礎**SyncLockWithStatusT**類別執行鎖定作業，該物件先等候物件可以使用。 此等待作業的結果會儲存在`status_`資料成員。 可能值`status_`資料成員是等候作業的傳回值。 如需詳細資訊，請參閱的傳回值`WaitForSingleObjectEx()`MSDN Library 中的函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)