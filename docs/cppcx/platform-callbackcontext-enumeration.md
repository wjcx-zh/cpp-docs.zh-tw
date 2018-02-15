---
title: "Platform:: callbackcontext 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9d34f7ef8a953ce60972c27b34e257ea66d62d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext 列舉
指定回呼函式 (事件處理常式) 會執行的執行緒內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum class CallbackContext {};  
```  
  
### <a name="members"></a>成員  
  
|類型程式碼|描述|  
|---------------|-----------------|  
|任何|回呼函式可以在任何執行緒的內容中執行。|  
|相同|回呼函式只能在啟動非同步作業的執行緒內容中執行。|  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd