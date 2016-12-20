---
title: "建立發行組建時的常見問題 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯組建, 與發行組建的不同"
  - "偵錯記憶體配置器"
  - "偵錯 [MFC], 發行組建"
  - "堆積配置問題"
  - "記憶體 [C++], 覆寫"
  - "MFC [C++], 發行組建"
  - "最佳化 [C++], 編譯器"
  - "指標, 偏離"
  - "專案 [C++], 偵錯組態"
  - "發行組建, 建置應用程式"
  - "發行組建, 疑難排解"
  - "偏離的指標"
  - "發行組建疑難排解"
  - "Visual C++ 疑難排解"
  - "未預期的程式碼產生"
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建立發行組建時的常見問題
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在開發期間，您通常會以專案的偵錯版進行建置及測試。  之後如果為您的應用程式建置發行的組建 \(Release Build\)，可能會發生存取違規。  
  
 下列清單顯示偵錯版與發行的組建 \(非偵錯\) 之間的主要差異。  當然還有其他差異，但以下是會導致應用程式在偵錯版中可正常執行，而在發行的組建中會失敗的主要差異。  
  
-   [堆積配置](#_core_heap_layout)  
  
-   [編譯](#_core_compilation)  
  
-   [指標支援](#_core_pointer_support)  
  
-   [最佳化](#_core_optimizations)  
  
 如需有關如何在偵錯版中找出發行組建錯誤的詳細資訊，請參閱 [\/GZ \(在偵錯版中找出發行組建的錯誤\)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) 編譯器選項。  
  
##  <a name="_core_heap_layout"></a> 堆積配置  
 當應用程式可在偵錯版中正常執行，而在發行的組建中卻不行時，大約有百分之九十的明顯問題是出自堆積 \(Heap\) 配置。  
  
 當您建置專案進行偵錯時，您是使用偵錯記憶體配置器 \(Debug Memory Allocator\)。  這表示所有的記憶體配置周圍都放置了保護位元組。  這些保護位元組會偵測記憶體覆寫。  由於發行的組建與偵錯版的堆積配置不同，在偵錯版中的記憶體覆寫可能不會造成任何問題，但在發行的組建中卻可能產生災難性的影響。  
  
 如需詳細資訊，請參閱[檢查記憶體覆寫](../../build/reference/checking-for-memory-overwrites.md)和[使用偵錯版檢查記憶體覆寫](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)。  
  
##  <a name="_core_compilation"></a> 編譯  
 當您建置發行的組建時，很多 MFC 巨集和眾多 MFC 實作都會變更。  尤其是 ASSERT 巨集在發行的組建中評估成不動作，因此將不會執行 ASSERT 中的任何程式碼。  如需詳細資訊，請參閱[檢查 ASSERT 陳述式](../../build/reference/using-verify-instead-of-assert.md)。  
  
 已內嵌 \(Inline\) 一些函式，以便在發行的組建中加快速度。  在發行的組建中通常會開啟最佳化。  並使用不同的記憶體配置器。  
  
##  <a name="_core_pointer_support"></a> 指標支援  
 缺少偵錯資訊時，會從您的應用程式中移除填補。  在發行的組建中，偏離的指標比較可能指向未初始化的記憶體，而非指向偵錯資訊。  
  
##  <a name="_core_optimizations"></a> 最佳化  
 根據程式碼的特定區段的本質，最佳化編譯器可能產生未預期的程式碼。  這是最不可能導致發行組建問題的原因，但它的確偶而會發生。  如需解決方案，請參閱[最佳化程式碼](../../build/reference/optimizing-your-code.md)。  
  
## 請參閱  
 [發行的組建](../../build/reference/release-builds.md)   
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)