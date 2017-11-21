---
title: "DontUseNewUseMake 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs: C++
helpviewer_keywords: DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 62f8abc151758ac9253698390cbab3e2ba62a4c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 類別
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>備註  
 禁止使用運算子`new`RuntimeClass 中。 因此，您必須使用[Make 函式](../windows/make-function.md)改為。  
  
## <a name="members"></a>成員  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new 運算子](../windows/dontusenewusemake-operator-new-operator.md)|多載運算子`new`並防止 RuntimeClass 中使用。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)   
 [Make 函式](../windows/make-function.md)