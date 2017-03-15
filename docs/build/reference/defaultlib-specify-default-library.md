---
title: "/DEFAULTLIB (指定預設程式庫) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.DefaultLibraries"
  - "/defaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEFAULTLIB 連結器選項"
  - "DEFAULTLIB 連結器選項"
  - "-DEFAULTLIB 連結器選項"
  - "程式庫, 加入至清單"
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /DEFAULTLIB (指定預設程式庫)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEFAULTLIB:library  
```  
  
## 備註  
 其中：  
  
 *library*  
 是在解析外部參考時所要搜尋的程式庫名稱。  
  
## 備註  
 \/DEFAULTLIB 選項會將一個 *library* 加入到 LINK 在解析參考時所搜尋的程式庫清單。  以 \/DEFAULTLIB 指定的程式庫會在命令列上所指定的程式庫之後，且在 .obj 檔中命名的預設程式庫之前被搜尋。  
  
 [忽略所有預設程式庫](../../build/reference/nodefaultlib-ignore-libraries.md) \(\/NODEFAULTLIB\) 選項會覆寫 \/DEFAULTLIB:*library*。  當兩者都指定了同樣的 *library* 名稱時，[忽略程式庫](../../build/reference/nodefaultlib-ignore-libraries.md) \(\/NODEFAULTLIB:*library*\) 選項會覆寫 \/DEFAULTLIB:*library*。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
-   Visual Studio 開發環境中沒有這個連結器選項。  若要在連結階段加入程式庫，請使用 \[輸入\] 屬性頁的 \[**其他相依性**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)