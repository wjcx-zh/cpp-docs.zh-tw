---
title: 'Platform:: failureexception 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
dev_langs:
- C++
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e644ec013b4beac6ebc4f7c774f926711dc1093e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609164"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException 類別
作業失敗時擲回。 這是 E_FAIL HRESULT 的對等用法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd  
  
## <a name="see-also"></a>另請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)