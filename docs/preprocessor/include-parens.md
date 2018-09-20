---
title: include （) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83f6bf58138a1e36e1c36131a448b456eb691c27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407578"
---
# <a name="include"></a>include()
**C + + 特定**  
  
停用自動排除。  
  
## <a name="syntax"></a>語法  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
### <a name="parameters"></a>參數  
*Name1*  
要強制包含的第一個項目。  
  
*Name2*  
要強制包含的第二個項目 (如果需要的話)。  
  
## <a name="remarks"></a>備註  
 
類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。 如果，也已被排除項目，如所示[編譯器警告 （層級 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)，而且它們不能有過，這個屬性可以用來停用自動排除。 這個屬性可以接受任意數目的引數，每個引數都會是要包含的類型程式庫項目名稱。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)