---
title: 排除 (#import) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5798c7515c411b9abf9d10229a6185e01bb92f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400194"
---
# <a name="exclude-import"></a>exclude (#import)
**C + + 特定**  
  
排除從類型程式庫標頭檔產生的項目。  
  
## <a name="syntax"></a>語法  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
### <a name="parameters"></a>參數  
*Name1*  
要排除的第一個項目。  
  
*Name2*  
要排除的第二個項目 (如果需要的話)。  
  
## <a name="remarks"></a>備註  
 
類型程式庫可能包含在系統標頭或其他類型程式庫中定義的項目。 這個屬性可以接受任意數目的引數，每一個都是要排除的頂層類型程式庫項目。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)