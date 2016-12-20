---
title: "_get_doserrno | Microsoft Docs"
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
  - "_get_doserrno"
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
  - "_get_doserrno"
  - "get_doserrno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_doserrno 函式"
  - "get_doserrno 函式"
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_doserrno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在作業系統傳回的錯誤值轉譯為 `errno` 值之前，傳回該錯誤值。  
  
## 語法  
  
```  
errno_t _get_doserrno(     int * pValue  );   
```  
  
#### 參數  
 \[out\] `pValue`  
 要填入 `_doserrno` 全域巨集之目前值的整數的指標。  
  
## 傳回值  
 若 `_get_doserrno` 成功，會傳回 0；若失敗，則傳回錯誤碼。  若 `pValue` 為 `NULL`，則會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## 備註  
 `_doserrno` 全域巨集會先在 CRT 初始化期間設為 0，再開始執行處理序。  此巨集是設定為由會傳回作業系統錯誤的任何系統層級函式呼叫所傳回的作業系統錯誤值，且在執行期間永不重設為 0。  當您撰寫程式碼以檢查函式傳回的錯誤值時，請在函式呼叫之前，先一律使用 [\_set\_doserrno](../../c-runtime-library/reference/set-doserrno.md) 清除 `_doserrno`。  因為其他函式呼叫可能會覆寫 `_doserrno`，因此請在函式呼叫之後立即使用 `_get_doserrno` 檢查值。  
  
 建議針對可攜式錯誤程式碼使用 [\_get\_errno](../../c-runtime-library/reference/get-errno.md)，而不是 `_get_doserrno`。  
  
 `_doserrno` 的可能值會定義在 \<errno.h\> 中。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_get_doserrno`|\<stdlib.h\>、\<cstdlib\> \(C\+\+\)|\<errno.h\>、\<cerrno\> \(C\+\+\)|  
  
 `_get_doserrno` 是 Microsoft 擴充功能。  如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [\_set\_doserrno](../../c-runtime-library/reference/set-doserrno.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)