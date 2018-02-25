---
title: "#錯誤指示詞 （C/c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e449da64b5221ccddee34dd850a987b28a2f39df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="error-directive-cc"></a>#error 指示詞 (C/C++)
`#error` 指示詞會在編譯時期發出使用者指定的錯誤訊息並終止編譯。  
  
## <a name="syntax"></a>語法  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>備註  
 這個指示詞會發出錯誤訊息包含*語彙基元字串*參數。 `token-string` 參數不是受巨集展開限制。 這個指示詞在前置處理期間最有用，可通知開發人員程式不一致或條件約束違規。 下列範例會示範前置處理期間的錯誤處理：  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)