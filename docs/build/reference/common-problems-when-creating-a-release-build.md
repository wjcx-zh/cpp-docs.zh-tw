---
title: 建立發行組建時的常見問題 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting Visual C++
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44b5528a2d6bedaaaa7ddce582f58042e084b3d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="common-problems-when-creating-a-release-build"></a>建立發行組建時的常見問題
在開發期間，您通常將建置和測試您的專案的偵錯組建。 如果您再建置您的應用程式的發行組建時，您可能會發生存取違規。  
  
 下列清單顯示偵錯和發行 （非偵錯） 組建的主要差異。 有其他差異，但以下是當它是在偵錯組建中，會導致失敗的應用程式在發行組建的主要差異。  
  
-   [堆積配置](#_core_heap_layout)  
  
-   [編譯](#_core_compilation)  
  
-   [指標的支援](#_core_pointer_support)  
  
-   [最佳化](#_core_optimizations)  
  
 請參閱[/GZ （攔截發行組建中的錯誤偵錯建置）](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md)如需如何攔截版本的編譯器選項建置偵錯組建中的錯誤。  
  
##  <a name="_core_heap_layout"></a>堆積配置  
 適用於偵錯，但未發行的應用程式時，堆積配置將會大約 90%的明顯問題的原因。  
  
 當您建置專案，以偵錯時，就使用偵錯記憶體配置器。 這表示所有記憶體配置都有保護位元組周圍都放置。 這些保護位元組偵測記憶體覆寫。 因為不同之間發行和偵錯堆積配置記憶體覆寫的版本可能不會在偵錯組建中，建立的任何問題，但在發行組建可能災難性的影響。  
  
 如需詳細資訊，請參閱[檢查記憶體覆寫](../../build/reference/checking-for-memory-overwrites.md)和[使用偵錯版檢查記憶體覆寫](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)。  
  
##  <a name="_core_compilation"></a>編譯  
 許多 MFC 巨集和大部分的 MFC 實作變更，當您建置發行版本。 特別是，ASSERT 巨集評估為 nothing 在發行組建，因此會執行任何判斷提示中的程式碼。 如需詳細資訊，請參閱[檢查 ASSERT 陳述式](../../build/reference/using-verify-instead-of-assert.md)。  
  
 有些功能會內嵌在發行組建加快速度。 通常會開啟最佳化發行組建中。 不同的記憶體配置器也會使用。  
  
##  <a name="_core_pointer_support"></a>指標的支援  
 缺乏偵錯資訊從您的應用程式中移除填補。 在發行組建，偏離的指標會有機會指向未初始化的記憶體，而不會將偵錯資訊。  
  
##  <a name="_core_optimizations"></a>最佳化  
 根據特定的程式碼區段的本質，最佳化編譯器可能會產生非預期的程式碼。 這是最不可能的原因的發行組建的問題，但在某些情況下，它並未發生。 如需解決方案，請參閱[最佳化程式碼](../../build/reference/optimizing-your-code.md)。  
  
## <a name="see-also"></a>請參閱  
 [發行組建](../../build/reference/release-builds.md)   
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)