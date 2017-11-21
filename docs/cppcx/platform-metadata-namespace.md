---
title: "Platform:: metadata 命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Metadata
dev_langs: C++
helpviewer_keywords: Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 7c108dd9435d433076ea2f2c9b573f2ebf3685e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="platformmetadata-namespace"></a>Platform::Metadata 命名空間
這個命名空間包含修改類型宣告的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
namespace Platform {  
   namespace Metadata {  
}}  
```  
  
### <a name="members"></a>成員  
 雖然此命名空間僅適合內部使用，但瀏覽器仍會顯示此命名空間的下列成員。  
  
|名稱|備註|  
|----------|------------|  
|屬性|屬性的基底類別。|  
|[Platform::Metadata::DefaultMemberAttribute 屬性](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|指出在許多可能的多載函式中要叫用的慣用函式。|  
|[Platform::Metadata::FlagsAttribute 屬性](../cppcx/platform-metadata-flagsattribute-attribute.md)Flags|宣告列舉為位元欄位的列舉。<br /><br /> 下列範例顯示如何將列舉套用至 `Flags` 屬性。<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|  
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|確保私用 ref 類別擁有有效的執行階段類別名稱。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Platform`  
  
### <a name="requirements"></a>需求  
 **中繼資料：** platform.winmd  
  
 **命名空間：** Platform::Metadata  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](platform-namespace-c-cx.md)