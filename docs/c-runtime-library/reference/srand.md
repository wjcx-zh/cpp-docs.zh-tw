---
title: "srand | Microsoft Docs"
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
  - "srand"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "srand"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "數字, 虛擬隨機"
  - "數字, 隨機"
  - "虛擬亂數"
  - "亂數, 產生"
  - "隨機起點"
  - "隨機起點, 設定"
  - "srand 函式"
  - "起點"
  - "起點, 設定隨機"
ms.assetid: 7bf56dc5-5692-4182-a3c1-18af98d2dd1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# srand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定虛擬亂數產生器的開頭之初始值。  
  
## 語法  
  
```  
void srand(  
   unsigned int seed   
);  
```  
  
#### 參數  
 `seed`  
 虛擬亂數產生的種子  
  
## 備註  
 `srand` 函式會設定開始點，以在目前執行緒產生一系列的虛擬隨機整數。  若要重新初始化產生器以建立結果的相同順序，請呼叫 `srand` 函式並再次使用相同的 `seed` 引數。  `seed` 的其他值將產生器設定成在虛擬隨機序列中不同的起點。  `rand` 擷取產生的虛擬亂數。  在呼叫 `rand` 前任何對 `srand` 的呼叫會產生與呼叫 `srand` 搭配 `seed` 傳為 1 相同的序列。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`srand`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [rand](../../c-runtime-library/reference/rand.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::Random 類別](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [rand](../../c-runtime-library/reference/rand.md)