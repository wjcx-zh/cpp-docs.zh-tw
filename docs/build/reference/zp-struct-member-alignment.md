---
title: "/Zp (結構成員對齊) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zp"
  - "VC.Project.VCCLCompilerTool.StructMemberAlignment"
  - "VC.Project.VCCLWCECompilerTool.StructMemberAlignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zp 編譯器選項 [C++]"
  - "結構成員對齊編譯器選項"
  - "Zp 編譯器選項"
  - "-Zp 編譯器選項 [C++]"
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Zp (結構成員對齊)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制結構成員如何裝入記憶體之中，並為模組中所有結構指定相同的封裝方式。  
  
## 語法  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## 備註  
 當您指定這個選項時，從第一個之後每一個結構成員都儲存於成員型別 \(Member Type\) 大小或 `n` 位元組界限 \(其中 `n` 為 1、2、4、8 或 16\)，以較小者為準。  
  
 下表中描述可使用的值。  
  
 1  
 在 1 位元組界限上封裝結構。  與 **\/Zp** 相同。  
  
 2  
 在 2 位元組界限上封裝結構。  
  
 4  
 在 4 位元組界限上封裝結構。  
  
 8  
 在 8 位元組界限上封裝結構 \(預設\)。  
  
 16  
 在 16 位元組界限上封裝結構。  
  
 除非您有特定的對齊需求，否則不應使用這個選項。  
  
 您也可以使用 [pack](../../preprocessor/pack.md) 控制結構的封裝。  如需對齊的詳細資訊，請參閱：  
  
-   [align](../../cpp/align-cpp.md)  
  
-   [\_\_alignof 運算子](../../cpp/alignof-operator.md)  
  
-   [\_\_unaligned](../../cpp/unaligned.md)  
  
-   [結構對齊範例](../../build/examples-of-structure-alignment.md) \(x64 專用\)  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**程式碼產生**\] 屬性頁。  
  
4.  修改 \[**結構成員對齊**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)