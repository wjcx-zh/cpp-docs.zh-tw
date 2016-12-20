---
title: "/Yl (插入偵錯程式庫的 PCH 參考) | Microsoft Docs"
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
  - "/yi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yl 編譯器選項 [C++]"
  - "Yl 編譯器選項 [C++]"
  - "-Yl 編譯器選項 [C++]"
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yl (插入偵錯程式庫的 PCH 參考)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在建立會使用先行編譯之標頭的偵錯程式庫且組建失敗時使用。  
  
## 語法  
  
```  
/Ylsymbol  
```  
  
```  
/Yl-  
```  
  
## Arguments  
 `symbol`  
 是要儲存在物件模組中的任意符號。  
  
 \-  
 減號 \(\-\) 明確停用 **\/Yl** 編譯器選項。  
  
## 備註  
 根據預設，編譯器會使用 **\/Yl** 選項 \(沒有指定 *symbol*\)。  **\/Yl** 選項可讓偵錯工具取得型別的完整資訊。  **\/Yl\-** 停用預設的行為。  
  
 以 **\/Yc** 和 **\/Yl**`symbol` 編譯模組時，編譯器會建立類似 \_\_@@\_PchSym\_@00@...@`symbol` 的符號，其中省略符號 \(...\) 表示連結器產生的字元字串，並將它儲存在物件模組中。  任何使用這個先行編譯標頭所編譯的原始程式檔 \(Source File\) 會參考您所指定的符號，使連結器包含此物件模組和程式庫的偵錯資訊。  
  
 使用這個選項，可能會產生 LNK1211。  指定 [\/Yc \(建立先行編譯標頭檔\)](../../build/reference/yc-create-precompiled-header-file.md) 和 [\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md) 選項時，編譯器會建立包含偵錯資訊的先行編譯標頭檔。  當您將先行編譯標頭儲存在程式庫，使用該程式庫建置物件模組，而且原始程式碼並未參考先行編譯標頭檔定義的任何函式時，就會發生錯誤。  
  
 若要解決這個問題，請在建立不包含任何函式定義的先行編譯標頭檔時，指定 **\/Yl**`symbol`，其中 `symbol` 是程式庫中任意符號的名稱。  這個選項是告訴編譯器將偵錯資訊儲存在先行編譯標頭檔中。  
  
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
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)