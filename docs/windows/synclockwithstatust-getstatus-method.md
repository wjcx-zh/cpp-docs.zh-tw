---
title: "SyncLockWithStatusT::GetStatus 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetStatus 方法"
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SyncLockWithStatusT::GetStatus 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 結構，而且不能直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>傳回值  
 上的物件，例如根據 SyncLockWithStatusT 類別中，以等候作業的結果 [Mutex](../windows/mutex-class1.md) 或 [號誌](../windows/semaphore-class.md)。 零 (0) 表示等待作業傳回信號的狀態。否則，另一個狀態發生，例如經過逾時值。  
  
## <a name="remarks"></a>備註  
 擷取目前的 SyncLockWithStatusT 物件的等候狀態。  
  
 GetStatus() 函式會擷取基礎值 [status_](../windows/synclockwithstatust-status-data-member.md) 資料成員。 當基礎 SyncLockWithStatusT 類別的物件執行鎖定作業時，物件會先等待變成可用物件。 此等待作業的結果會儲存在 `status_` 資料成員。 可能的值 `status_` 資料成員會等候作業的傳回值。 如需詳細資訊，請參閱的傳回值 **WaitForSingleObjectEx()** MSDN Library 中的函式。  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)