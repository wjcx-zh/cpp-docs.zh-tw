---
title: "如何： 偵錯發行組建 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31113d9a5935536ac10b22c7b5f5af27b0d29970
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-debug-a-release-build"></a>如何：偵錯發行的組建
您可以偵錯應用程式的發行組建。  
  
### <a name="to-debug-a-release-build"></a>若要偵錯發行組建  
  
1.  開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**C/c + +**節點。 設定**偵錯資訊格式**至[C7 相容 (/ Z7)](../../build/reference/z7-zi-zi-debug-information-format.md)或**程式資料庫 (/Zi)**。  
  
3.  展開**連結器**按一下**一般**節點。 設定**啟用累加連結**至[否 (/ /INCREMENTAL: NO)](../../build/reference/incremental-link-incrementally.md)。  
  
4.  選取**偵錯**節點。 設定**產生偵錯資訊**至[是 (/debug)](../../build/reference/debug-generate-debug-info.md)。  
  
5.  選取**最佳化**節點。 設定**參考**至[/opt: ref](../../build/reference/opt-optimizations.md)和**啟用 COMDAT 摺疊**至[/opt: icf](../../build/reference/opt-optimizations.md)。  
  
6.  您現在可以偵錯發行組建的應用程式。 若要找出問題時，逐步執行程式碼 （或使用時間恰好偵錯），直到您找出失敗的發生，然後判斷不正確的參數或程式碼。  
  
     如果應用程式是在偵錯組建中，但在發行組建時失敗，編譯器最佳化的其中一個可能會公開在原始碼的缺失。 若要找出問題，請停用所選取的每個原始程式碼檔的最佳化直到您找出檔案，導致此問題的最佳化。 （若要加速此程序，您可以將檔案分割成兩個群組、 停用其中一個群組，在最佳化和您在群組中，發現問題時繼續進行分割，直到您分辨出問題的檔案。）  
  
     您可以使用[/RTC](../../build/reference/rtc-run-time-error-checks.md)嘗試公開這類偵錯組建中的 bug。  
  
     如需詳細資訊，請參閱[最佳化程式碼](../../build/reference/optimizing-your-code.md)。  
  
## <a name="see-also"></a>請參閱  
 [解決發行組建的問題](../../build/reference/fixing-release-build-problems.md)