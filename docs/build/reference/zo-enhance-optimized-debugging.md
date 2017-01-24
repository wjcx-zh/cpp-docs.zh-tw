---
title: "/Zo (增強最佳化的偵錯) | Microsoft Docs"
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
  - "-Zo"
  - "/Zo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zo 編譯器選項 [C++]"
  - "Zo 編譯器選項 [C++]"
  - "-Zo 編譯器選項 [C++]"
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zo (增強最佳化的偵錯)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在非偵錯組建中產生適用於最佳化程式碼的增強型偵錯資訊。  
  
## 語法  
  
```cpp  
/Zo[-]  
```  
  
## 備註  
 **\/Zo**編譯器參數會產生適用於最佳化程式碼的增強型偵錯資訊。  最佳化可能會將暫存器用於區域變數、重新排列程式碼、向量化迴圈和內嵌函式呼叫。  這些最佳化可能會混淆原始程式碼與已編譯的目的碼之間的關係。  **\/Zo** 參數會指示編譯器為區域變數和內嵌函式產生額外的偵錯資訊。  當您在 Visual Studio 偵錯工具中逐步執行最佳化程式碼時，可使用它來查看 \[**自動變數**\]、\[**區域變數**\] 和 \[**監看式**\] 視窗。  它也能在 WinDBG 偵錯工具中啟用堆疊追蹤以顯示內嵌函式。  當指定 [\/Od](../../build/reference/od-disable-debug.md) 時，已停用最佳化的偵錯組建 \(**\/Zo**\) 不需要產生其他偵錯資訊。  使用 **\/Zo** 參數以啟動最佳化來偵錯發行組態。  如需最佳化參數的詳細資訊，請參閱 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)。  當您使用 **\/Zi** 或 **\/Z7** 指定偵錯資訊時，在 Visual Studio 2015 中依預設會啟用 **\/Zo** 選項。  指定 **\/Zo\-** 以明確停用此編譯器選項。  
  
 **\/Zo** 參數可在 Visual Studio 2013 Update 3 中取得，且會取代先前未記載的 **\/d2Zi\+** 參數。  
  
### 若要在 Visual Studio 中設定 \/Zo 編譯器選項  
  
1.  開啟專案的 \[屬性頁\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[配置屬性\]、\[C\/C\+\+\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[其他選項\] 屬性以包含 `/Zo`，然後選擇 \[確定\]。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../../build/reference/z7-zi-zi-debug-information-format.md)   
 [編輯後繼續](../Topic/Edit%20and%20Continue.md)