---
title: __security_init_cookie | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __security_init_cookie
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
dev_langs:
- C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 249fc38a36ee0f3a61b6347b48219154bada7d22
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="securityinitcookie"></a>__security_init_cookie
初始化全域安全性 Cookie。  
  
## <a name="syntax"></a>語法  
  
```  
void __security_init_cookie(void);  
```  
  
## <a name="remarks"></a>備註  
 全域安全性 Cookie 用於在以 [/GS (緩衝區安全性檢查)](../../build/reference/gs-buffer-security-check.md) 編譯的程式碼以及在使用例外狀況處理的程式碼中，提供緩衝區滿溢保護。 在進入滿溢保護的函式時，此 Cookie 會放在堆疊上，然後結束時，在堆疊上的值會與全域 Cookie 進行比較。 它們之間的任何差異表示已發生緩衝區滿溢，並導致程式立即終止。  
  
 一般而言，`__security_init_cookie` 初始化時會由 CRT 呼叫它。 如果您略過 CRT 初始化 (例如，如果您使用 [/ENTRY](../../build/reference/entry-entry-point-symbol.md) 指定進入點)，則必須自行呼叫 `__security_init_cookie`。 如果沒有呼叫 `__security_init_cookie`，會將全域安全性 Cookie 設定為預設值，且緩衝區滿溢保護會遭到入侵。 由於攻擊者可以利用此預設 Cookie 值擊敗緩衝區滿溢檢查，所以建議您定義您自己的進入點時務必呼叫 `__security_init_cookie`。  
  
 必須先呼叫`__security_init_cookie`，才能輸入任何滿溢保護的函式；否則將會偵測到假性的緩衝區滿溢。 如需詳細資訊，請參閱 [C 執行階段錯誤 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)。  
  
## <a name="example"></a>範例  
 請參閱 [C 執行階段錯誤 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) 中的範例。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`__security_init_cookie`|\<process.h>|  
  
 `__security_init_cookie` 是標準的 C 執行階段程式庫的 Microsoft 擴充功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Compiler Security Checks In Depth](http://go.microsoft.com/fwlink/?linkid=7260) (深入了解編譯器安全性檢查)
