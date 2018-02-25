---
title: "inject_statement |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dacc2867b767495c608789b9efbe23bf7aa7110
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="injectstatement"></a>inject_statement
**C + + 特定的**  
  
 將其做為來源文字的引數插入至類型程式庫標題。  
  
## <a name="syntax"></a>語法  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>參數  
 `source_text`  
 要插入至類型程式庫標題檔案的來源文字。  
  
## <a name="remarks"></a>備註  
 文字會放置在命名空間宣告的開頭位置，該命名空間宣告會在標題檔案中包裝類型程式庫內容。  
  
 **END c + + 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)