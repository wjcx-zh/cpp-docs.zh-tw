---
title: "auto_gcroot 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs: C++
helpviewer_keywords: auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bd39306e7a56506937d0084ee3167ab121eb26c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="autogcroot-class"></a>auto_gcroot 類別
自動資源管理 (例如[auto_ptr 類別](../standard-library/auto-ptr-class.md)) 可用來將原生類型中嵌入虛擬控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>參數  
 `_element_type`  
 要內嵌的 managed 的類型。  
  
## <a name="requirements"></a>需求  
 **標頭檔** \<msclr\auto_gcroot.h >  
  
 **命名空間**msclr  
  
## <a name="see-also"></a>另請參閱  
 [auto_gcroot](../dotnet/auto-gcroot.md)   
 [auto_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [如何： 宣告原生類型中的控制代碼](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle 類別](../dotnet/auto-handle-class.md)