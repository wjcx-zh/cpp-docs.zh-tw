---
title: "feholdexcept2 | Microsoft Docs"
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
  - "feholdexcept"
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
  - "feholdexcept"
  - "fenv/feholdexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feholdexcept 函式"
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# feholdexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將目前的浮點環境儲存在指定的物件、 清除浮點狀態旗標，可能的話，請將放置於非停止模式浮點數的環境。  
  
## 語法  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
  
```  
  
#### 參數  
 `penv`  
 指標 `fenv_t` 物件，以包含浮點環境的複本。  
  
## 傳回值  
 如果且只有函式是能夠順利開啟非停止浮點例外狀況處理，則傳回零。  
  
## 備註  
 `feholdexcept` 函式用來儲存目前的浮動點環境的狀態 `fenv_t` 指向的物件 `penv`, ，並設定環境設定，不會中斷執行浮點例外狀況。 這稱為非停止模式。  這個模式會繼續執行，直到將環境還原使用 [fesetenv](../Topic/fesetenv2.md) 或 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)。  
  
 您可以使用此函式必須隱藏從呼叫端的一或多個浮點例外狀況的副程式開頭。 若要報告例外狀況，只要清除不想要的例外狀況使用 [feclearexcept，](../../c-runtime-library/reference/feclearexcept1.md) ，然後就結束非停止模式，藉由呼叫 `feupdateenv`。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`feholdexcept`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](../Topic/fesetenv2.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)