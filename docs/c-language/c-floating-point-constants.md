---
title: "C 浮點常數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "常數, 浮點"
  - "double 資料類型, 浮點常數"
  - "浮點常數"
  - "浮點常數, 關於浮點常數"
  - "浮點數, 浮點常數"
  - "類型 [C], 常數"
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 浮點常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「浮點常數」表示帶正負號的十進位實數。  帶正負號實數的表示由整數部分、小數部分和指數部分所組成。  使用浮點常數表示不能變更的浮點值。  
  
## 語法  
 *符點常數*:  
 *小數常數 指數部分*  可選               *浮動後置字元*  可選  
  
 *數字序列 指數部分 浮動後置字元*  可選  
  
 *小數常數*:  
 *數字序列*  可選               **.**  *數字序列*  
  
 *數字序列*  **.**  
  
 *指數部分*:  
 **e**  *正負號*  可選               *數字序列*  
  
 **E**  *正負號*  可選               *數字序列*  
  
 *正負號* :擇一  
 **\+ –**  
  
 *數字序列* :  
 *digit*  
  
 *數值數字序列*  
  
 *浮動後置字元* :擇一  
 **f l F L**  
  
 您可以省略小數點 \(值的整數部分前\) 前的數字或小數點 \(分數部分\) 之後的數字，但不能同時省略兩者。  當您包含指數時才可以忽略小數點。  空白字元不能用於分隔常數的數值或字元。  
  
 下列範例說明浮點常數和表達式的某些形式:  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 浮點常數是正數，除非在減號 \(**–**\) 之後。  在這種情況下，負號視為一元算術負運算子。  浮點常數有 **float**和 **double**或者 `long double`型別。  
  
 沒有 **f**和 **F**和 **l**或 **L** 結尾的浮點常數為 **double**型別。  如果 **f** 字母或 **F** 是後置字元，常數為 **float**型別。  如果字尾加入字母 **l** 或 **L**，它具有 `long double`型別。  例如：  
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 請注意 Microsoft C 編譯器將 **long double** 轉換至 **double**型別。  如需型別 **double**和 **float**和 **long**的詳細資訊，請參閱 [基本型別的儲存](../c-language/storage-of-basic-types.md) 。  
  
 如下列範例所示，您可以省略浮點常數的整數部分。  小數 .75 可以用許多方式表示，包括下列:  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## 請參閱  
 [C 常數](../c-language/c-constants.md)