---
title: 'Platform:: idisposable 介面 |Microsoft Docs'
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3899c25d71ad08cc058280271080c19d11222ed
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589782"
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