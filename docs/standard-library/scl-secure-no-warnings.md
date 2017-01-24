---
title: "_SCL_SECURE_NO_WARNINGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_SCL_SECURE_NO_DEPRECATE"
  - "_SCL_SECURE_NO_WARNINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_SCL_SECURE_NO_DEPRECATE"
  - "_SCL_SECURE_NO_WARNINGS"
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _SCL_SECURE_NO_WARNINGS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

呼叫任何一個可能不安全的方法在 Standard C\+\+ 程式庫中產生 [編譯器警告 \(層級 3\) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。  若要停用這項警告，請定義巨集 **\_SCL\_SECURE\_NO\_WARNINGS** 程式碼:  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## 備註  
 其他方式停用警告 C4996 包括:  
  
-   使用 [\/D \(前置處理器定義\)](../build/reference/d-preprocessor-definitions.md) 編譯器選項:  
  
    ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
    ```  
  
-   使用 [\/w](../build/reference/compiler-option-warning-level.md) 編譯器選項:  
  
    ```  
    cl /wd4996 [other compiler options] myfile.cpp  
    ```  
  
-   使用 [\#pragma warning](../preprocessor/warning.md) 指示詞:  
  
    ```  
    #pragma warning(disable:4996)  
    ```  
  
 此外，您也可以手動變更標準警告與 **\/w\<l\>\<n\>** 編譯器選項的 C4996。  例如，將警告 C4996 到層級 4:  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 如需詳細資訊，請參閱[\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../build/reference/compiler-option-warning-level.md)。  
  
## 請參閱  
 [安全程式庫：C\+\+ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)