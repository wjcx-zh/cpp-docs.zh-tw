---
title: "連結器工具錯誤 LNK1309 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1309"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1309"
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具錯誤 LNK1309
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵測到 type1 模組；有參數 \/CLRIMAGETYPE:type2 無效  
  
 已經以 **\/CLRIMAGETYPE** 要求 CLR 映像型別，但是由於一個或多個模組與該型別不相容，連結器無法產生該型別的影像。  
  
 例如，如果指定 **\/CLRIMAGETYPE:safe**，而且用 **\/clr:pure** 傳遞模組組建，就會看到 LNK1309。  
  
 如果您嘗試使用 ptrustu\[d\].lib 建置部分信任的 CLR 純應用程式，也會看到 LNK1309。  如需如何建立部分信任的應用程式之詳細資訊，請參閱 [如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式](../../dotnet/create-a-partially-trusted-application.md)。  
  
 如需詳細資訊，請參閱[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)與[\/CLRIMAGETYPE \(指定 CLR 映像類型\)](../../build/reference/clrimagetype-specify-type-of-clr-image.md)。