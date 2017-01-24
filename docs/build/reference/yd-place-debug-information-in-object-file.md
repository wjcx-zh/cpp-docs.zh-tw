---
title: "/Yd (將偵錯資訊置入目的檔) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yd 編譯器選項 [C++]"
  - "偵錯 [C++], 偵錯資訊檔案"
  - "Yd 編譯器選項 [C++]"
  - "-Yd 編譯器選項 [C++]"
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yd (將偵錯資訊置入目的檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配合 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 和 [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) 選項使用時，會將完整的偵錯資訊置入所有由先行編譯標頭 \(.pch\) 檔建立的目的檔中。  已取代。  
  
## 語法  
  
```  
/Yd  
```  
  
## 備註  
 **\/Yd** 已被取代；[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 現在支援多個物件寫入單一 .pdb 檔，請改用 **\/Zi**。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
 除非您需要散發包含偵錯資訊的程式庫，否則請使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 選項，而不要用 **\/Z7** 和 **\/Yd**。  
  
 只有在散發含有偵錯資訊的程式庫時才需要將完整的偵錯資訊儲存在每一個 .obj 檔案中。  它會減緩編譯速度並且需要相當大的磁碟空間。  當使用 **\/Yc** 和 **\/Z7** 而不搭配 **\/Yd** 時，編譯器會將通用偵錯資訊儲存在由 .pch 檔案建立的 .obj 檔案中。  編譯器不會將這項資訊插入由 .pch 檔案後續建立的 .obj 檔案中；它會插入這項資訊的交互參考。  不論有多少 .obj 檔案使用 .pch 檔案，只有一個 .obj 檔案會含有通用偵錯資訊。  
  
 雖然這項預設行為會產生較快的組建時間並且減少磁碟空間的需求，但是如果有項小變更需要重建含有通用偵錯資訊的 .obj 檔案的話就會很麻煩了。  在這種情況下，編譯器必須重建含有對原來 .obj 檔案之交互參考的所有 .obj 檔案。  同時，如果某個通用 .pch 檔案被不同的專案使用時，要依賴對單一 .obj 檔案的交互參考會相當困難。  
  
 如需先行編譯標頭的詳細資訊，請參閱：  
  
-   [\/Y \(先行編譯標頭\)](../../build/reference/y-precompiled-headers.md)  
  
-   [建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 範例  
 假設您有兩個主檔案 F.cpp 和 G.cpp，每一個都含有以下 **\#include** 陳述式：  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 以下命令會建立先行編譯標頭檔 ETC.pch 和目的檔 F.obj：  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 目的檔 F.obj 包含了 WINDOWS.h 和 ETC.h \(以及它們包含的任何其他標頭檔 \(Header File\)\) 的型別和符號資訊。  現在您可以使用先行編譯標頭 ETC.pch 來編譯原始程式檔 G.cpp：  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 目的檔 G.obj 並未包含先行編譯標頭的偵錯資訊，只是參考 F.obj 檔案中的這項資訊。  請注意，您必須以 F.obj 檔案連結。  
  
 如果您的先行編譯標頭不是以 **\/Z7** 編譯，您仍然可以在稍後使用 **\/Z7** 的編譯中使用它。  不過，偵錯資訊會置於目前的目的檔中，而且偵錯工具無法使用先行編譯標頭中定義的函式區域符號和型別。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)