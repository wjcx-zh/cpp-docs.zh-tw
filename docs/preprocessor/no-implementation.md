---
title: no_implementation |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c882a8d4eb2510969401b4280eb66116ad220c77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440832"
---
# <a name="noimplementation"></a>no_implementation
**C + + 特定**  
  
不產生 .tli 標頭，其中包含包裝函式成員函式的實作。  
  
## <a name="syntax"></a>語法  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>備註  
 
如果已指定這個屬性，則會產生 .tlh 標頭 (具有公開類型程式庫項目的宣告)，但沒有 `#include` 陳述式可包含 .tli 標頭檔。  
  
這個屬性用於搭配[implementation_only](../preprocessor/implementation-only.md)。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)