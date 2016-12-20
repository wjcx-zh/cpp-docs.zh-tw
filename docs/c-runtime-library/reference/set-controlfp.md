---
title: "_set_controlfp | Microsoft Docs"
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
  - "_set_controlfp"
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
  - "set_controlfp"
  - "_set_controlfp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_controlfp 函式"
  - "浮點函式, 設定控制字組"
  - "set_controlfp 函式"
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_controlfp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定浮點控制字。  
  
## 語法  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### 參數  
 `newControl`  
 新的控制字位元值。  
  
 `mask`  
 設置的新控制字位元的遮罩。  
  
## 傳回值  
 無。  
  
## 備註  
 `_set_controlfp` 與 `_control87`類似，不過，它只設定浮點控制字至 `newControl`。  位元值表示浮點控制項狀態。  浮點控制狀態使應用程式得以改變浮點數學套件的精準度，捨入，以及無限模式。  您也可以使用 `_set_controlfp` 於浮點例外狀況的遮罩或去遮罩。  如需詳細資訊，請參閱[\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)。  
  
 這個函式現在已不建議在 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md) 或 `/clr:pure` 下編譯時使用，因為 Common Language Runtime 只支援預設浮點精準度。  
  
## 需求  
  
|常式|必要的標頭|相容性|  
|--------|-----------|---------|  
|`_set_controlfp`|\<float.h\>|只支援 x86 處理器|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_clear87、\_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_status87、\_statusfp、\_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)