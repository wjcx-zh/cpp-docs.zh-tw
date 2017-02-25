---
title: "fesetenv1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fesetenv"
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
  - "fesetenv"
  - "fenv/fesetenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fesetenv 函式"
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# fesetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定目前的浮點環境。  
  
## 語法  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
  
```  
  
#### 參數  
 `penv`  
 指標 `fenv_t` 物件，包含浮點數的環境設定，藉由呼叫 [fegetenv](../Topic/fegetenv2.md) 或 [feholdexcept](../Topic/feholdexcept1.md)。 您也可以指定預設啟動浮點環境使用 FE\_DFL\_ENV 巨集。  
  
## 傳回值  
 如果成功設定環境，則傳回 0。 否則，傳回非零值。  
  
## 備註  
 `fesetenv` 函式會將目前的浮點環境中儲存的值從 `fenv_t` 指向的物件 `penv`。 浮點點環境是一組狀態旗標和影響浮點計算的控制項模式。 這包括捨入模式和浮點例外狀況的狀態旗標。 如果 `penv` 不 FE\_DFL\_ENV 或不是指向有效 `fenv_t` 物件時，後續的行為是未定義。  
  
 呼叫此函式設定的例外狀況中的狀態旗標 `penv` 物件，但它不會引發這些例外狀況。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fesetenv`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)