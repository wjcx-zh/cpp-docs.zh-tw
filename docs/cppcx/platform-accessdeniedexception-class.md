---
title: 'Platform:: accessdeniedexception 類別 |Microsoft 文件'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4be26bfc87be55d36954429c64094cabd6a6cf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException 類別
當存取資源或功能遭拒時擲回。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
### <a name="remarks"></a>備註  
 如果您遇到此例外狀況，請確定您已要求適當的功能，並且已在應用程式的封裝資訊清單中執行必要的宣告。 如需詳細資訊，請參閱 [COMException](../cppcx/platform-comexception-class.md) 類別。  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd  
  
## <a name="see-also"></a>另請參閱  
 [Platform::COMException 類別](../cppcx/platform-comexception-class.md)