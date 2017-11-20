---
title: "Platform:: delegate 類別 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Delegate
dev_langs: C++
helpviewer_keywords: Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d7bdd03cef8aab0344cf3fa72ef40341c11287d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="platformdelegate-class"></a>Platform::Delegate 類別
表示函式物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public delegate void delegate_name();  
```  
  
### <a name="members"></a>成員  
 委派類別具有衍生自 [Platform::Object Class](../cppcx/platform-object-class.md)的 Equals()、GetHashCode() 和 ToString() 方法。  
  
### <a name="remarks"></a>備註  
 使用 [委派](../windows/delegate-cpp-component-extensions.md) 關鍵字建立委派，請勿明確使用 Platform::Delegate。 如需詳細資訊，請參閱[委派](../cppcx/delegates-c-cx.md)。 如需如何建立和使用委派的範例，請參閱 [Creating Windows Runtime Components in C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)。  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)