---
title: "連結器工具警告 LNK4098 | Microsoft Docs"
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
  - "LNK4098"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4098"
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4098
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

預設的程式庫 'library' 與其他使用的程式庫衝突；請使用 \/NODEFAULTLIB:library  
  
 您嘗試連結不相容的程式庫。  
  
> [!NOTE]
>  現在執行階段程式庫包含指示詞，可避免混合不同類型的程式庫。  如果您嘗試在同一個程式中使用不同類型、或偵錯與非偵錯版本的執行階段程式庫，就會出現這個警告。  例如，如果您編譯了一個使用執行階段程式庫的檔案，而其他檔案使用的是其他種類 \(例如單一執行緒與多執行緒\) 的執行階段程式庫，就會出現這個警告。  您應該用相同的執行階段程式庫來編譯所有的原始程式檔。  如需詳細資訊，請參閱[使用執行階段程式庫](../../build/reference/md-mt-ld-use-run-time-library.md) \(**\/MD**、**\/MT**、**\/LD**\) 編譯器選項。  
  
 您可以用連結器的 [\/VERBOSE:LIB](../../build/reference/verbose-print-progress-messages.md) 參數來決定連結器應該搜尋哪一個程式庫。  如果接到 LNK4098 的警告，而且想要建立使用單一執行緒或非偵錯執行階段程式庫之類的可執行檔，請使用 **\/VERBOSE:LIB** 選項，找出連結器所要搜尋的程式庫。  連結器在搜尋程式庫時，應該會列印出 LIBC.lib，而不是 LIBCMT.lib、MSVCRT.lib、LIBCD.lib、LIBCMTD.lib 或 MSVCRTD.lib。  您可以對每個想要忽略的程式庫使用 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) 選項，通知連結器忽略不正確的 Run\-Time 程式庫。  
  
 下表顯示您在想用哪些執行階段程式庫時應該忽略哪些程式庫。  
  
|若要使用這個執行階段程式庫|請忽略這些程式庫|  
|-------------------|--------------|  
|單一執行緒 \(libc.lib\)|libcmt.lib、msvcrt.lib、libcd.lib、libcmtd.lib、msvcrtd.lib|  
|多執行緒 \(libcmt.lib\)|libc.lib、msvcrt.lib、libcd.lib、libcmtd.lib、msvcrtd.lib|  
|使用 DLL \(msvcrt.lib\) 的多執行緒|libc.lib、libcmt.lib、libcd.lib、libcmtd.lib、msvcrtd.lib|  
|偵錯單一執行緒 \(libcd.lib\)|libc.lib、libcmt.lib、msvcrt.lib、libcmtd.lib、msvcrtd.lib|  
|偵錯多執行緒 \(libcmtd.lib\)|libc.lib、libcmt.lib、msvcrt.lib、libcd.lib、msvcrtd.lib|  
|使用 DLL 的偵錯多執行緒 \(msvcrtd.lib\)|libc.lib、libcmt.lib、msvcrt.lib、libcd.lib、libcmtd.lib|  
  
 例如，如果您收到這個警告，而想要建立一個使用非偵錯、單一執行緒版本執行階段程式庫的可執行檔，您可以使用下列連結器選項：  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```