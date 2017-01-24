---
title: "/F (設定堆疊大小) | Microsoft Docs"
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
  - "/f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/F 編譯器選項 [C++]"
  - "F 編譯器選項 [C++]"
  - "-F 編譯器選項 [C++]"
  - "set stack size 編譯器選項"
  - "堆疊, 設定大小"
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /F (設定堆疊大小)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以位元組為單位設定程式堆疊大小。  
  
## 語法  
  
```  
/F number  
```  
  
## Arguments  
 `number`  
 是以位元組為單位的堆疊大小。  
  
## 備註  
 不使用這個選項的話，堆疊大小會預設值為 1 MB。  引數 `number` 可以是十進位或者 C 語言標記法。  引數的範圍可以從 1 一直到連結器能夠接受的最大堆疊大小。  連結器會將指定的值進位至最接近 4 的倍數個位元組。  **\/F** 與 `number` 之間的空格可有可無。  
  
 如果您的程式產生了堆疊溢位的訊息，您可能需要增加堆疊的大小。  
  
 您也可以利用下列方式設定堆疊大小：  
  
-   使用 **\/STACK** 連結器選項。  如需詳細資訊，請參閱[\/STACK](../../build/reference/stack.md)。  
  
-   在 .exe 檔案上使用 EDITBIN。  如需詳細資訊，請參閱[EDITBIN 參考](../../build/reference/editbin-reference.md)。  
  
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