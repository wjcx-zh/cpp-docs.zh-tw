---
title: no_namespace |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02919e1e96717c1accc6343ecff32a66968cbcc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378811"
---
# <a name="nonamespace"></a>no_namespace
**C + + 特定**  
  
指定命名空間名稱不是由編譯器產生。  
  
## <a name="syntax"></a>語法  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>備註  
 
`#import` 標頭檔中的類型程式庫內容通常是在命名空間中定義。 中指定的命名空間名稱`library`陳述式的原始 IDL 檔案。 如果**no_namespace**指定屬性，則此命名空間不由編譯器產生。  
  
如果您想要使用不同的命名空間的名稱，然後使用[rename_namespace](../preprocessor/rename-namespace.md)改為屬性。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)