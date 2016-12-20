---
title: "fegetround、fesetround | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fegetround"
  - "fesetround"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fegetround"
  - "fesetround"
  - "fenv/fegetround"
  - "fenv/fesetround"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fegetround 函式"
  - "fesetround 函式"
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fegetround、fesetround
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得或設定目前的浮點捨入模式。  
  
## 語法  
  
```  
int fegetround(void);  
  
int fesetround(  
   int round_mode  
);   
```  
  
#### 參數  
 `round_mode`  
 要以其中一個浮點捨入巨集形式設定的捨入模式。 如果值不等於其中一個浮點捨入巨集，就不會變更捨入模式。  
  
## 傳回值  
 成功時，`fegetround` 會以其中一個浮點捨入巨集值的形式傳回捨入模式。 如果無法判斷目前的捨入模式，它就會傳回負值。  
  
 如果成功， `fesetround` 會傳回 0。 否則，會傳回非零值。  
  
## 備註  
 浮點運算可以使用數種捨入模式的其中之一。 這些項目會控制在儲存結果時浮點運算結果的捨入方向。 以下是 \<fenv.h\> 中所定義之浮點捨入巨集的名稱和行為：  
  
|巨集|描述|  
|--------|--------|  
|FE\_DOWNWARD|捨入為無限大的負數。|  
|FE\_TONEAREST|捨入為最接近的數字。|  
|FE\_TOWARDZERO|以趨近於零的方式捨入。|  
|FE\_UPWARD|捨入為無限大的正數。|  
  
 FE\_TONEAREST 的預設行為會使用雙數 \(0\) 最低有效位元，將結果捨入為介於可表示的值和最接近的值之間。  
  
 目前的捨入模式會影響下列作業：  
  
-   字串轉換。  
  
-   常數運算式之外的浮點算術運算子結果。  
  
-   程式庫捨入函式，例如 `rint` 和 `nearbyint`。  
  
-   從標準程式庫數學函式傳回值。  
  
 目前的捨入模式不會影響下列作業：  
  
-   `trunc`、`ceil`、`floor` 和 `lround` 程式庫函式。  
  
-   浮點至整數隱含轉型和轉換，其一律會以趨近於零的方式捨入。  
  
-   常數運算式中浮點算術運算子的結果，其一律會捨入為最接近的值。  
  
 若要使用這些函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fegetround`, `fesetround`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [nearbyint、 nearbyintf、 nearbyintl](../../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)   
 [rint、rintf、rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)   
 [lrint、 lrintf、 lrintl、 llrint、 llrintf、 llrintl](../../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)