---
title: "SRWLock 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs: C++
helpviewer_keywords: SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6721620490a00da0b9c8fa039be0379f4d7dd1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="srwlock-class"></a>SRWLock 類別
代表輕型的讀取器/寫入器鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>備註  
 輕型的讀取器/寫入器鎖定用來同步存取之物件或資源的執行緒上。 如需詳細資訊，請參閱[同步函式](http://msdn.microsoft.com/en-us/9b6359c2-0113-49b6-83d0-316ad95aba1b)。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|||  
|-|-|  
|**SyncLockExclusive**|SRWLock 物件取得獨佔模式中的同義字。|  
|**SyncLockShared**|取得以共用模式的 SRWLock 物件的同義字。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[SRWLock::SRWLock 建構函式](../windows/srwlock-srwlock-constructor.md)|初始化 SRWLock 類別的新執行個體。|  
|[SRWLock::~SRWLock 解構函式](../windows/srwlock-tilde-srwlock-destructor.md)|取消初始化 SRWLock 類別的執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[SRWLock::LockExclusive 方法](../windows/srwlock-lockexclusive-method.md)|取得 SRWLock 物件以獨佔模式。|  
|[SRWLock::LockShared 方法](../windows/srwlock-lockshared-method.md)|取得 SRWLock 物件以共用模式。|  
|[SRWLock::TryLockExclusive 方法](../windows/srwlock-trylockexclusive-method.md)|嘗試取得 SRWLock 中的物件目前或指定 SRWLock 物件的獨佔模式。|  
|[SRWLock::TryLockShared 方法](../windows/srwlock-trylockshared-method.md)|嘗試取得 SRWLock 中的物件目前或指定 SRWLock 物件的共用模式。|  
  
### <a name="protected-data-member"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[SRWLock::SRWLock_ 資料成員](../windows/srwlock-srwlock-data-member.md)|包含目前 SRWLock 物件基礎的鎖定變數。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `SRWLock`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)