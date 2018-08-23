---
title: inject_statement |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4142b742ae6c2a758c2a2fb5e09c604959433f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539000"
---
# <a name="injectstatement"></a>inject_statement
**C + + 特定**  
  
將其做為來源文字的引數插入至類型程式庫標題。  
  
## <a name="syntax"></a>語法  
  
```  
inject_statement("source_text")  
```  
  
### <a name="parameters"></a>參數  
*source_text*  
要插入至類型程式庫標題檔案的來源文字。  
  
## <a name="remarks"></a>備註  
 
文字會放置在命名空間宣告的開頭位置，該命名空間宣告會在標題檔案中包裝類型程式庫內容。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)