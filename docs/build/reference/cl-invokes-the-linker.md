---
title: "CL 叫用連結器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 編譯器 [C++], 編譯而不連結"
  - "cl.exe 編譯器 [C++], 控制連結器"
  - "編譯原始程式碼 [C++], 沒有連結"
  - "從編譯器叫用連結器"
  - "LINK 工具 [C++], 從 CL 編譯器叫用"
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# CL 叫用連結器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果沒有使用 \/c 選項，CL 會在編譯之後自動叫用連結器。  CL 會將編譯過程中產生的 .obj 檔檔名以及命令列上指定之任何其他檔案名稱傳遞給連結器。  連結器會使用 LINK 環境變數中所列的選項。  您可以使用 \/link 選項在 CL 命令列上指定連結器選項。  在 \/link 選項之後的選項會強制取代 LINK 環境變數中的選項。  下表中的選項會抑制連結。  
  
|選項|說明|  
|--------|--------|  
|\/c|編譯而不連結|  
|\/E、\/EP、\/P|前置處理而不編譯或連結|  
|\/Zg|產生函式原型 \(Prototype\)|  
|\/Zs|檢查語法|  
  
 如需有關連結的詳細資訊，請參閱[連結器選項](../../build/reference/linker-options.md)。  
  
## 範例  
 假設您要編譯三個 C 原始程式檔：MAIN.c、MOD1.c 和 MOD2.c。  每個檔案都會呼叫一個定義在不同檔案中之函式：  
  
-   MAIN.c 會呼叫 MOD1.c 中的函式 `func1` 以及 MOD2.c 中的函式 `func2`。  
  
-   MOD1.c 會呼叫標準程式庫函式 `printf_s` 和 `scanf_s`。  
  
-   MOD2.c 會呼叫定義於 MYGRAPH.lib 程式庫中，名為 `myline` 和 `mycircle` 的圖形函式。  
  
 若要建置這個程式，請以下列命令列編譯：  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL 首先會編譯 C 原始程式檔並且產生目的檔 MAIN.obj、MOD1.obj 及 MOD2.obj。  編譯器會將標準程式庫的名稱置入每一個 .obj 檔中。  如需詳細資訊，請參閱[使用執行階段程式庫](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 CL 會將 .obj 檔的名稱併同 MYGRAPH.lib 名稱一起傳遞給連結器。  連結器會將外部參考解析如下：  
  
1.  在 MAIN.obj 中，對 `func1` 的參考會使用 MOD1.obj 中的定義解析；對 `func2` 的參考會使用 MOD2.obj 中的定義解析。  
  
2.  在 MOD1.obj 中，對 `printf_s` 和 `scanf_s` 的參考會使用連結器從 MOD1.obj 中找到名稱的程式庫中的定義解析。  
  
3.  在 MOD2.obj 中，對 `myline` 和 `mycircle` 的參考會使用 MYGRAPH.lib 中的定義解析。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)