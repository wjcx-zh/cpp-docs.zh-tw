---
title: "Platform:: idisposable 介面 |Microsoft 文件"
ms.custom: 
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::IDisposable
dev_langs: C++
helpviewer_keywords: Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db500bc5a205b97ba49d92356d2e878be3e10caf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable 介面
用來釋放 Unmanaged 資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>屬性  
 **GuidAttribute**(「 de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
 **VersionAttribute**(NTDDI_WIN8)  
  
### <a name="members"></a>成員  
 IDisposable 介面繼承自 IUnknown 介面。 IDisposable 也有下列類型的成員：  
  
 **方法**  
  
 IDisposable 介面具有下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|Dispose|用來釋放 Unmanaged 資源。|  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform