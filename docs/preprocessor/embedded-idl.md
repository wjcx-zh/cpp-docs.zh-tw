---
title: embedded_idl |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e0b594952e8e5be0a9be9c843877c8c4bb95eca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="embeddedidl"></a>embedded_idl
**C + + 特定的**  
  
 指定類型程式庫將寫入 .tlh 檔，並保留屬性產生的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
embedded_idl[("param")]  
```  
  
#### <a name="parameters"></a>參數  
 `param`  
 可以是下列兩個值之一：  
  
-   emitidl: 從 typelib 匯入的類型資訊會出現在針對屬性化專案產生的 IDL 中。  這是預設值，如果未指定 `embedded_idl` 的參數就會生效。  
  
-   no_emitidl: 從 typelib 匯入的類型資訊不會出現在針對屬性化專案產生的 IDL 中。  
  
## <a name="example"></a>範例  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## <a name="remarks"></a>備註  
 **END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)