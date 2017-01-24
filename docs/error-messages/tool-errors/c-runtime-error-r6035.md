---
title: "C 執行階段錯誤 R6035 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6035"
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 執行階段錯誤 R6035
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft Visual C\+\+ 執行階段程式庫，錯誤 R6035：當這個應用程式的模組正在初始化此模組的全域安全性 Cookie 的同時，依賴此安全性 Cookie 的函式正在使用中。要早一點呼叫 \_\_security\_init\_cookie。  
  
 在初次使用此全域安全性 Cookie 之前，必須要先呼叫 [\_\_security\_init\_cookie](../../c-runtime-library/reference/security-init-cookie.md)。  
  
 此全域安全性 Cookie 是用來當做以 [\/GS \(緩衝區安全性檢查\)](../../build/reference/gs-buffer-security-check.md) 編譯的程式碼及使用結構化例外狀況處理之程式碼中的緩衝區滿溢保護。  基本上來說，在進入有滿溢保護的函式中時，會將此 Cookie 放在堆疊上，而在結束時，會將堆疊上的值與全域 Cookie 做比較。  比較所得的任何差異表示已發生緩衝區滿溢，而這會讓程式立即終止。  
  
 錯誤 R6035 表示在進入受保護的函式之後，已對 `__security_init_cookie` 發出了呼叫。  如果繼續執行，將會偵測到假造的緩衝區滿溢，因為堆疊上的 Cookie 不再符合此全域 Cookie。  
  
 請參考下列 DLL 範例。  透過連結器 [\/ENTRY \(進入點符號\)](../../build/reference/entry-entry-point-symbol.md) 選項，將 DLL 進入點設定為 DllEntryPoint。  如此會略過 CRT 的初始化作業 \(此作業通常會初始化全域安全性 Cookie\)，因此必須由 DLL 本身來呼叫 `__security_init_cookie`。  
  
```  
// Wrong way to call __security_init_cookie  
DllEntryPoint(...) {  
   DllInitialize();  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
  
void DllInitialize() {  
   __security_init_cookie();  
}  
```  
  
 此範例將會產生錯誤 R6035，因為 DllEntryPoint 會使用結構化例外狀況處理，因此會使用安全性 Cookie 來偵測緩衝區滿溢。  當呼叫 DllInitialize 時，此全域安全性 Cookie 便已經放在堆疊上。  
  
 以下範例將示範進行這項處理的正確方式：  
  
```  
// Correct way to call __security_init_cookie  
DllEntryPoint(...) {  
   __security_init_cookie();  
   DllEntryHelper();  
}  
  
void DllEntryHelper() {  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
```  
  
 在此例中，DllEntryPoint 不會受到防止緩衝區滿溢的保護 \(它沒有任何本機字串緩衝區，也不會使用結構化例外狀況處理\)；因此，它可以安心地呼叫 `__security_init_cookie`。  然後，它會呼叫受到保護的 Helper 函式。  
  
> [!NOTE]
>  錯誤訊息 R6035 只會由 x86 偵錯 CRT 產生，而且只針對結構化例外狀況處理 \(但是其情況是在所有平台上發生錯誤\)，以及針對所有形式的例外狀況處理，例如 C\+\+ EH。  
  
## 請參閱  
 [編譯器安全檢查詳解](http://go.microsoft.com/fwlink/?linkid=7260)