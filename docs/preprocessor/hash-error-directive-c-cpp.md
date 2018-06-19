---
title: '#錯誤指示詞 （C/c + +） |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4f0e06798bc6419f8db0471f19588039eb679a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33905568"
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
  
## <a name="see-also"></a>另請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)