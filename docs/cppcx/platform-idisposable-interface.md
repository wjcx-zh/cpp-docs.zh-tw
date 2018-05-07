---
title: 'Platform:: idisposable 介面 |Microsoft 文件'
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68c5425d5d65acc194287a97068df7da15f37275
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable 介面
用來釋放 Unmanaged 資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>屬性  
 **GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
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