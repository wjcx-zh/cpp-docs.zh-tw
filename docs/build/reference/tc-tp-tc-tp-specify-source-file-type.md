---
title: "/Tc、/Tp、/TC、/TP (指定原始程式檔類型) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.CompileAs"
  - "VC.Project.VCCLCompilerTool.CompileAs"
  - "/Tp"
  - "/tc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Tc 編譯器選項 [C++]"
  - "/Tp 編譯器選項 [C++]"
  - "原始程式檔, 指定至編譯器"
  - "Tc 編譯器選項 [C++]"
  - "-Tc 編譯器選項 [C++]"
  - "Tp 編譯器選項 [C++]"
  - "-Tp 編譯器選項 [C++]"
ms.assetid: 7d9d0a65-338b-427c-8b48-fff30e2f9d2b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Tc、/Tp、/TC、/TP (指定原始程式檔類型)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

雖然沒有 .c 副檔名，**\/Tc** 選項還是指定 `filename` 為 C 原始程式檔。  雖然沒有 .cpp 或 .cxx 副檔名，**\/Tp** 選項還是指定 `filename` 為 C\+\+ 原始程式檔。  選項與 `filename` 之間的空格是選擇性的。  每一選項指定一個檔案；若要指定其他檔案，請重複這個選項。  
  
 **\/TC** 和 **\/TP** 是 **\/Tc** 和 **\/Tp** 的全域 Variant。  它們向編譯器指定，將命令列上提名的所有檔案視為 C 原始程式檔 \(**\/TC**\) 或 C\+\+ 原始程式檔 \(**\/TP**\)，而與選項在命令列上的位置無關。  這些全域選項可以在單一檔案上，透過 **\/Tc** 或 **\/Tp** 加以覆寫。  
  
## 語法  
  
```  
/Tcfilename  
/Tpfilename  
/TC  
/TP  
```  
  
## Arguments  
 `filename`  
 是一個 C 或 C\+\+ 原始程式檔。  
  
## 備註  
 根據預設，CL 會假設具有 .c 副檔名的檔案是 C 原始程式檔，而具有 .cpp 或 .cxx 副檔名的檔案是 C\+\+ 原始程式檔。  
  
 當 **TC** 選項 或 **Tc** 選項擇一指定時， [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 選項的所有規格會被忽略。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**進階**\] 屬性頁。  
  
4.  修改 \[**編譯為**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。  
  
## 範例  
 以下 CL 命令列是指定 MAIN.c、TEST.prg 和 COLLATE.prg 全部都是 C 原始程式檔。  CL 不會辨識 PRINT.prg。  
  
```  
CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG  
```  
  
 以下 CL 命令列是指定 TEST1.c、TEST2.cxx、TEST3.huh 和 TEST4.o 要編譯為 C\+\+ 檔案，而 TEST5.z 則編譯為 C 檔案。  
  
```  
CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP  
```  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)