---
title: "/Yu (使用先行編譯標頭檔) | Microsoft Docs"
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
  - "/yu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案, 使用現有的"
  - "/Yu 編譯器選項 [C++]"
  - "PCH 檔案, 使用現有的"
  - "先行編譯標頭檔, 使用現有的"
  - "Yu 編譯器選項 [C++]"
  - "-Yu 編譯器選項 [C++]"
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yu (使用先行編譯標頭檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示編譯器在目前的編譯中使用現有的先行編譯標頭檔 \(.pch\)。  
  
## 語法  
  
```  
/Yu[filename]  
```  
  
## Arguments  
 *filename*  
 標頭檔的名稱，是使用 **\#include** 前置處理器指示詞包含在原始程式檔中。  
  
## 備註  
 對於建立先行編譯標頭的 **\/Yc** 選項以及表示使用先行編譯標頭的任何後續 **\/Yu** 選項，include 檔的名稱都必須相同。  
  
 `filename` 會為 **\/Yc** 指定先行編譯停止的點；編譯器會透過 `filename` 先行編譯所有程式碼，並使用 include 檔的主檔名和副檔名 .pch 為所產生的先行編譯標頭命名。  
  
 該 .pch 檔一定是使用 **\/Yc** 所建立的。  
  
 編譯器會將發生於 .h 檔案之前的所有程式碼視為已先行編譯。  它會直接跳過與 .h 檔案相關聯的 **\#include** 指示詞，使用 .pch 檔案中包含的程式碼，然後編譯 `filename`.之後的所有程式碼。  
  
 在命令列上，**\/Yu** 與 `filename` 之間不可以有空格。  
  
 當您不用檔名指定 **\/Yu** 選項時，原始程式必須包含指定先行編譯標頭檔名 \(.pch 檔\) 的 [\#pragma hdrstop](../../preprocessor/hdrstop.md) Pragma。  在這種情況下，編譯器將會使用由 [\/Fp \(命名 .Pch 檔案\)](../../build/reference/fp-name-dot-pch-file.md) 指名的先行編譯標頭 \(.pch 檔案\)。  編譯器會跳到該 Pragma 的位置，從 Pragma 指定的先行編譯標頭檔還原編譯的狀態，然後僅編譯 Pragma 後面的程式碼。  如果 **\#pragma hdrstop** 沒有指定檔名，編譯器會尋找具有從原始程式檔主檔名加上 .pch 副檔名所衍生檔名的檔案。  您也可以使用 **\/Fp** 選項，指定不同的 .pch 檔案。  
  
 如果不用檔名指定 **\/Yu**，也沒有指定 **hdrstop** Pragma，就會產生錯誤訊息而且編譯也會失敗。  
  
 如果 **\/Yc**`filename` 和  **\/Yu**`filename` 選項發生在相同的命令列上，而且同時參考相同的檔案名稱，**\/Yc**`filename` 會取得優先而先行編譯所有程式碼一直到 \(並包含\) 指名的檔案。  這項功能簡化了 Makefile 的撰寫。  
  
 因為 .pch 檔案包含有關電腦環境的資訊，以及有關程式的記憶體位址資訊，所以您只能使用位於建立此檔案之電腦上的 pch 檔。  
  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [\/Y \(先行編譯標頭\)](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  在專案中的 .cpp 檔上指定 [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md)。  
  
2.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
3.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
4.  按一下 \[**先行編譯標頭**\] 屬性頁。  
  
5.  修改 \[**透過檔案建立\/使用 PCH**\] 屬性或 \[**建立\/使用先行編譯標頭檔**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A>以及<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>。  
  
## 範例  
 如果下列程式碼：  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 是使用 `CL /YuMYAPP.H PROG.CPP` 進行編譯，編譯器不會處理三個 Include 陳述式，而是從 MYAPP.pch 使用先行編譯程式碼，節省了前置處理這三個檔案 \(及其可能包含的任何檔案\) 所耗費的時間。  
  
 如果 .pch 檔案的名稱與 **\/Yc** 的檔名引數或原始程式檔的主檔名都不相同，您可以使用 [\/Fp \(命名 .Pch 檔案\)](../../build/reference/fp-name-dot-pch-file.md) 選項配合 **\/Yu** 選項，指定 .pch 檔案的名稱，如下所示：  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 這個命令會指定名為 MYPCH.pch 的先行編譯標頭檔。  編譯器會使用它的內容，還原所有標頭檔的先行編譯狀態一直到 \(並且包含\) MYAPP.h。  然後編譯器再編譯發生於 MYAPP.h **include** 陳述式之後的程式碼。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)