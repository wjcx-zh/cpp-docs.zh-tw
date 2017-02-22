---
title: "fegetenv1 | Microsoft Docs"
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
  - "fetegenv"
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
  - "fegetenv"
  - "fenv/fegetenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fetegenv 函式"
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# fegetenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將目前的浮點環境儲存在指定的物件。  
  
## 語法  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### 參數  
 `penv`  
 指標 `fenv_t` 物件，以包含目前環境的浮點值。  
  
## 傳回值  
 傳回 0，表示的浮點數的環境中成功儲存在 `penv`。 否則，傳回非零值。  
  
## 備註  
 `fegetenv` 函式中所指向的物件會儲存目前的浮點環境 `penv`。 浮點點環境是一組狀態旗標和影響浮點計算的控制項模式。 這包括捨入方向模式和浮點例外狀況的狀態旗標。 如果 `penv` 不是指向有效 `fenv_t` 物件時，後續的行為是未定義。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fegetenv`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)