---
title: "feupdateenv | Microsoft Docs"
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
  - "feupdateenv"
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
apitype: "HeaderDef"
f1_keywords: 
  - "feupdateenv"
  - "fenv/feupdateenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feupdateenv 函式"
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# feupdateenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

儲存目前引發的浮點例外狀況，還原指定的浮點數環境狀態，並接著會引發儲存浮點例外狀況。  
  
## 語法  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
#### 參數  
 `penv`  
 指標 `fenv_t` 物件，包含浮點數的環境設定，藉由呼叫 [fegetenv](../Topic/fegetenv2.md) 或 [feholdexcept](../Topic/feholdexcept1.md)。 您也可以指定預設啟動浮點環境使用 FE\_DFL\_ENV 巨集。  
  
## 傳回值  
 如果順利完成所有動作，則傳回 0。 否則，傳回非零值。  
  
## 備註  
 `feupdateenv` 函式會執行多個動作。 首先，它會自動儲存體中儲存目前引發的浮點例外狀況狀態旗標。 然後，它會設定目前的浮點環境中儲存的值從 `fenv_t` 指向的物件 `penv`。 如果 `penv` 不 FE\_DFL\_ENV 或不是指向有效 `fenv_t` 物件時，後續的行為是未定義。 最後， `feupdateenv` 引發儲存在本機的浮點例外狀況。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`feupdateenv`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)