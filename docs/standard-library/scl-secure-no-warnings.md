---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 285e54a2eab4d116df81c3e10c597c6dbb6dd9cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
呼叫 C++ 標準程式庫中任一種可能不安全的方法將會產生 [編譯器警告 (層級 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 若要停用此警告，請在程式碼中定義 **_SCL_SECURE_NO_WARNINGS** 巨集：  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>備註  
 停用警告 C4996 的其他方式包括：  
  
-   使用 [/D (前置處理器定義)](../build/reference/d-preprocessor-definitions.md) 編譯器選項：  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   使用 [/w](../build/reference/compiler-option-warning-level.md) 編譯器選項：  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   使用 [#pragma warning](../preprocessor/warning.md) 指示詞：  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 此外，您可以手動變更與警告 C4996 的層級**/w\<l >\< n>** 編譯器選項。 例如，若要將 C4996 警告設為層級 4：  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../build/reference/compiler-option-warning-level.md)。  
  
## <a name="see-also"></a>請參閱  
 [安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)

