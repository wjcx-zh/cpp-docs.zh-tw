---
title: no_auto_exclude |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67d077ca620661ffda2e8664b2a4fb9ef5ea7168
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408254"
---
# <a name="noautoexclude"></a>no_auto_exclude
**C + + 特定**  
  
停用自動排除。  
  
## <a name="syntax"></a>語法  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>備註  
 
類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 `#import` 會自動排除這類項目以嘗試避開多個定義錯誤。 這麼做，當[編譯器警告 （層級 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)將發出的每個要排除的項目。 您可以使用這個屬性停用這種自動排除行為。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)