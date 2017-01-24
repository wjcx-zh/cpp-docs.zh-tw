---
title: "編譯器控制的 LINK 選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器 [C++], 控制連結器"
  - "cl.exe 編譯器 [C++], 影響連結的功能"
  - "LINK 工具 [C++], 編譯器控制選項"
  - "連結器 [C++], CL 編譯器控制項"
  - "連結 [C++], 受到 CL 功能的影響"
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器控制的 LINK 選項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除非您指定了 \/c 選項，否則 CL 編譯器會自動呼叫 LINK。  CL 透過命令列選項和引數提供了一些對連結器的控制  下表摘要了一些 CL 中會影響連結的功能。  
  
|CL 規格|影響 LINK 的 CL 動作|  
|-----------|---------------------|  
|除 .c、.cxx、.cpp 或 .def 以外的任何副檔名|將檔名當做輸入傳遞給 LINK|  
|*filename*.def|傳遞 \/DEF:*filename*.def|  
|\/F`number`|傳遞 \/STACK:`number`|  
|\/Fd*filename*|傳遞 \/PDB:*filename*|  
|\/Fe*filename*|傳遞 \/OUT:*filename*|  
|\/Fm*filename*|傳遞 \/MAP:*filename*|  
|\/Gy|建立封裝函式 \(Packaged Function\) \(COMDAT\)；啟用函式層級連結 \(Function\-Level Linking\)|  
|\/LD|傳遞 \/DLL|  
|\/LDd|傳遞 \/DLL|  
|\/link|傳遞命令列的其餘部分給 LINK|  
|\/MD 或 \/MT|將預設程式庫名稱置於 .obj 檔中|  
|\/MDd 或 \/MTd|將預設程式庫名稱置於 .obj 檔中。  定義符號 **\_DEBUG**|  
|\/nologo|傳遞 \/NOLOGO|  
|\/Zd|傳遞 \/DEBUG|  
|\/Zi 或 \/Z7|傳遞 \/DEBUG|  
|\/Zl|從 .obj 檔省略預設程式庫名稱|  
  
 如需詳細資訊，請參閱[編譯器選項](../../build/reference/compiler-options.md)。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)