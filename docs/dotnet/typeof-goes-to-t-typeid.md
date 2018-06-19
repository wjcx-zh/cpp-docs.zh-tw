---
title: 'typeof 變成 t:: typeid |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0ae9f772a68735555748e6edbeb6196f1a73d2c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164514"
---
# <a name="typeof-goes-to-ttypeid"></a>typeof 變成 T::typeid
`typeof`用於 Managed Extensions for 具有已經由一般 c + + 運算子`typeid`Visual c + + 中的關鍵字。  
  
 在 Managed Extensions，`__typeof()`運算子會傳回相關聯`Type*`物件時傳遞的 managed 型別名稱。 例如:   
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 在新語法中，`__typeof`已由其他形式的取代`typeid`傳回`Type^`指定 managed 型別時。  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## <a name="see-also"></a>另請參閱  
 [一般的語言變更 (C + + /CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)