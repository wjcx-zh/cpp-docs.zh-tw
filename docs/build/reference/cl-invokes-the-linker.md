---
title: CL 叫用連結器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc9c5c4815dc83b37d0b7971d5fd0f31db51e39e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371911"
---
# <a name="cl-invokes-the-linker"></a>CL 叫用連結器
CL 自動叫用編譯除非使用了 /c 選項之後的連結器。 編譯期間建立的.obj 檔案的名稱以及任何其他命令列上指定的檔案名稱，CL 會傳遞至連結器。 連結器會使用 LINK 環境變數中所列的選項。 您可以使用 /link 選項指定 CL 命令列上的連結器選項。 /Link 選項後面接著的選項會覆寫 LINK 環境變數中。 下表中的選項會抑制連結。  
  
|選項|描述|  
|------------|-----------------|  
|/c|編譯而不連結|  
|/ / 電子，/EP，P|前置處理，而不編譯或連結|  
|/Zg|產生函式原型|  
|/Zs|請檢查語法|  
  
 如需連結的詳細資訊，請參閱[連結器選項](../../build/reference/linker-options.md)。  
  
## <a name="example"></a>範例  
 假設您編譯 C 三個原始程式檔： MAIN.c、 MOD1.c 和 MOD2.c。 每個檔案包含不同的檔案中定義的函式的呼叫：  
  
-   MAIN.c 呼叫函式`func1`MOD1.c 和函式中`func2`MOD2.c 中。  
  
-   標準程式庫函式會呼叫 MOD1.c`printf_s`和`scanf_s`。  
  
-   MOD2.c 呼叫圖形函式，名為`myline`和`mycircle`，這會定義名為 MYGRAPH.lib 文件庫中。  
  
 若要建置此程式，請使用下列命令列編譯：  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 CL 先編譯 C 原始程式檔，並建立 MAIN.obj、 MOD1.obj 和 MOD2.obj 物件檔案。編譯器會將每個.obj 檔案的標準程式庫名稱。 如需詳細資訊，請參閱[使用執行階段程式庫](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
 CL 將.obj 檔案，以及名稱 MYGRAPH.lib，名稱傳遞至連結器。 連結器會解析外部參考，如下所示：  
  
1.  MAIN.obj，參考中`func1`MOD1.obj; 中使用的定義進行解析的參考`func2`MOD2.obj 中使用的定義進行解析。  
  
2.  中的參考，MOD1.obj`printf_s`和`scanf_s`解決連結器會尋找名為 MOD1.obj 內程式庫中使用的定義。  
  
3.  中的參考，MOD2.obj`myline`和`mycircle`解決 MYGRAPH.lib 中使用的定義。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)