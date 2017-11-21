---
title: "CriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection
dev_langs: C++
helpviewer_keywords: CriticalSection class
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89587f87bd71d2688bba2c128d28c01212b50b71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="criticalsection-class"></a>CriticalSection 類別
代表關鍵區段的物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CriticalSection;  
```  
  
## <a name="members"></a>成員  
  
### <a name="constructor"></a>建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CriticalSection::CriticalSection 建構函式](../windows/criticalsection-criticalsection-constructor.md)|初始化同步處理物件類似於 mutex 物件，但可用來在單一處理序執行緒。|  
|[CriticalSection::~CriticalSection 解構函式](../windows/criticalsection-tilde-criticalsection-destructor.md)|取消初始化與目前 CriticalSection 物件已遭終結。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CriticalSection::TryLock 方法](../windows/criticalsection-trylock-method.md)|嘗試進入重要區段，而不會封鎖。 如果呼叫成功，則呼叫的執行緒會關鍵區段的擁有權。|  
|[CriticalSection::Lock 方法](../windows/criticalsection-lock-method.md)|等候指定的重要區段物件的擁有權。 函數會傳回擁有權授與呼叫執行緒時。|  
|[CriticalSection::IsValid 方法](../windows/criticalsection-isvalid-method.md)|指出目前的重要區段是否有效。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CriticalSection::cs_ 資料成員](../windows/criticalsection-cs-data-member.md)|宣告重要區段的資料成員。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CriticalSection`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)