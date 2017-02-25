---
title: "嚴重錯誤 C1189 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1189"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1189"
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 嚴重錯誤 C1189
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#error : 使用者提供的錯誤訊息  
  
 C1189 是由 `#error` 指示詞產生。  撰寫指示詞的程式開發人員會指定錯誤訊息文字。  如需詳細資訊，請參閱[\#error 指示詞](../../preprocessor/hash-error-directive-c-cpp.md)。  
  
 下列範例會產生 C1189。  在範例中，因為未定義 `_WIN32` 識別項，開發人員發出自訂錯誤訊息：  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 如果使用 **\/robust** MIDL 編譯器選項來建置 ATL 專案的話，可能也會出現這個錯誤訊息。  使用 **\/robust** 參數建立 [!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)] 和 Windows 中最新版本。  若要更正此錯誤，請使用下列程序。  
  
-   變更 dlldatax.c 檔案中的這行程式碼：  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 變更為：  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   使用 \[**MIDL**\] 屬性頁資料夾中的 \[**進階**\] 屬性頁，移除 **\/robust** 參數，然後指定 **\/no\_robust** 參數。  如需詳細資訊，請參閱[MIDL 屬性頁：進階](../../ide/midl-property-pages-advanced.md)。  
  
## 請參閱  
 [\#define 指示詞](../../preprocessor/hash-define-directive-c-cpp.md)