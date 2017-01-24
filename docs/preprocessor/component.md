---
title: "元件 | Microsoft Docs"
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
  - "vc-pragma.component"
  - "component_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "component pragma"
  - "Pragma, 元件"
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 元件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從原始程式檔內部收集瀏覽資訊或相依性資訊的控制項。  
  
## 語法  
  
```  
  
      #pragma component( browser, { on | off }[, references [, name ]] )  
#pragma component( minrebuild, on | off )  
#pragma component( mintypeinfo, on | off )  
```  
  
## 備註  
  
## 瀏覽器  
 您可以開啟或關閉收集功能，而且可以指定要在收集的資訊中忽略的特定名稱。  
  
 使用開啟或關閉來控制收集 pragma 前方的瀏覽資訊。  例如：  
  
```  
#pragma component(browser, off)  
```  
  
 讓編譯器停止收集瀏覽資訊。  
  
> [!NOTE]
>  若要使用此 pragma 開啟瀏覽資訊的收集，請參閱[必須先啟用瀏覽資訊](../build/reference/building-browse-information-files-overview.md)。  
  
 **references** 選項可以包含或不包含 *name* 引數。  使用不含 *name* 的 **references** 會開啟或關閉參考的收集 \(但是仍繼續收集其他瀏覽資訊\)。  例如：  
  
```  
#pragma component(browser, off, references)  
```  
  
 讓編譯器停止收集參考資訊。  
  
 使用含有 *name* 和 **off**  的 **references** 可防止 *name*  的參考出現在瀏覽資訊視窗。  使用這個語法會忽略您沒有興趣的名稱和類型，並可減少瀏覽資訊檔的大小。  例如：  
  
```  
#pragma component(browser, off, references, DWORD)  
```  
  
 從該處忽略前方 **DWORD**  的參考。  您可以使用 **on** 重新開啟收集 `DWORD` 的參考：  
  
```  
#pragma component(browser, on, references, DWORD)  
```  
  
 這是唯一可以繼續收集 *name* 之參考的方式，您必須明確開啟已關閉的任何 *name* 。  
  
 若要避免前置處理器擴展 *name* \(例如將 **NULL** 擴展為 **0**\)，請在其前後放置引號：  
  
```  
#pragma component(browser, off, references, "NULL")  
```  
  
## 最少重建  
 Visual C\+\+ 最少重建功能需要編譯器建立和儲存 C\+\+ 類別相依性資訊，這會佔用磁碟空間。  為了節省磁碟空間，您可以在不需要收集相依性資訊時使用 `#pragma component( minrebuild, off )` ，例如，不會變更的標頭檔。  在不會變更的類別之後插入 `#pragma component(minrebuild, on)` ，可重新開啟相依性集合。  
  
## 減少類型資訊  
 **mintypeinfo** 選項可減少指定區域的偵錯資訊。  這項資訊的容量相當可觀，會影響到 .pdb 和 .obj 檔案。  您無法在 mintypeinfo 區域中偵錯類別和結構。  使用 mintypeinfo 選項可避免下列警告：  
  
```  
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information  
```  
  
 如需詳細資訊，請參閱[啟用最少重建](../build/reference/gm-enable-minimal-rebuild.md) \(\/Gm\) 編譯器選項。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)