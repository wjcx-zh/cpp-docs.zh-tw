---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: e2f39c4f07235c75204a63e634053f887682337e
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

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
  
 此外，您可以使用 **/w\<l>\<n>** 編譯器選項，手動變更 C4996 警告的層級。 例如，若要將 C4996 警告設為層級 4：  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 如需詳細資訊，請參閱 [/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)](../build/reference/compiler-option-warning-level.md)。  
  
## <a name="see-also"></a>另請參閱  
 [安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)


