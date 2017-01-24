---
title: "連結器工具錯誤 LNK1211 | Microsoft Docs"
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
  - "LNK1211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1211"
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到先行編譯型別資訊；未連結或覆寫 'filename'。  
  
 以 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 編譯的指定目的檔並未指定於 LINK 命令中，或已被覆寫。  
  
 如果您正在建立一個使用先行編譯標頭的偵錯程式庫，且指定了 \/Yc 和 [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，Visual C\+\+ 便會產生一個包含 CodeView 偵錯資訊的先行編譯目的檔。  這個錯誤只會發生在下列這種情形，即當您將先行編譯的目的檔儲存在程式庫，接著使用該程式庫建置一個可執行檔的映像，而被參考到的目的檔卻不具有任一該先行編譯目的檔定義函式的可轉移參考。  
  
 解決這種情況有下列兩種方法：  
  
-   指定 [\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) 編譯器選項，將先行編譯標頭的 CodeView 資訊加入至每個物件模組。  這種方法較不建議使用，因為這麼做會產生大型的物件模組，增加連結應用程式所需的時間。  
  
-   在建立一個不含任何函式定義的先行編譯標頭檔 \(Precompiled Header File\) 時，指定 [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 並傳入任一自訂字串的名稱。  這樣便可引導編譯器在先行編譯目的檔中建立一個符號，並在每個使用與先行編譯目的檔相關的先行編譯標頭檔的目的檔發出該符號的參考。  
  
 當您使用 **\/Yc** 和 **\/Yl** 編譯模組時，編譯器會建立類似 `__@@_PchSym_@00@...@symbol_name` 的符號 \(其中的刪節號 \(...\) 表示編譯器產生的字元字串\)，並將其存放於物件模組中。  任何使用這個先行編譯標頭所編譯的原始程式檔 \(Source File\) 會參考您所指定的符號，使連結器包含此物件模組和程式庫的偵錯資訊。  
  
 如需此錯誤的詳細資訊，請參閱知識庫 \(Knowledge Base\) 文件 Q102697 PRB: Build Errors Using Precompiled Header in Debugging Lib。