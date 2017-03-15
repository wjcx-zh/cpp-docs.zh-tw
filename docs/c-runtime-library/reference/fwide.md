---
title: "fwide | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwide"
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
apitype: "DLLExport"
f1_keywords: 
  - "fwide"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fwide 函式"
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fwide
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未實作。  
  
## 語法  
  
```  
int fwide(  
   FILE *stream,  
   int mode;  
);  
```  
  
#### 參數  
 `stream`  
 in `FILE` 結構的指標 \(忽略\)。  
  
 `mode`  
 資料流的新寬度:寬字元，位元組的非正數，零未變更離開。\(這個值會被忽略。\)  
  
## 傳回值  
 這個函式會傳回 `mode`。  
  
## 備註  
 這個函式版本不符合標準。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fwide`|\<wchar.h\>|  
  
 如需詳細的相容性資訊，請參閱[Compatibility](../../c-runtime-library/compatibility.md)。