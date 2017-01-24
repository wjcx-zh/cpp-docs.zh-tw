---
title: "/GT (支援 Fiber-Safe 執行緒區域儲存區) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations"
  - "/gt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GT 編譯器選項 [C++]"
  - "Fiber-Safe 靜態執行緒區域儲存區譯器選項 [C++]"
  - "GT 編譯器選項 [C++]"
  - "-GT 編譯器選項 [C++]"
  - "靜態執行緒區域儲存區和 Fiber Safety"
  - "執行緒區域儲存區"
ms.assetid: 071fec79-c701-432b-9970-457344133159
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GT (支援 Fiber-Safe 執行緒區域儲存區)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

對使用靜態執行緒區域儲存區配置的資料 \(亦即以 `__declspec(thread)` 配置的資料\) 支援 Fiber 安全性。  
  
## 語法  
  
```  
/GT  
```  
  
## 備註  
 以 `__declspec(thread)` 宣告的資料是透過執行緒區域儲存區 \(TLS\) 陣列參考。  TLS 陣列是系統對每一執行緒維持的位址陣列。  這個陣列中的每一個位址都提供了執行緒區域儲存區資料的位置。  
  
 Fiber 是由一個堆疊和一個暫存器內容組成的輕量物件，並且可以排程在各種執行緒上。  Fiber 可以在任何執行緒上執行。  由於 Fiber 可能會交換出去，然後再在另一個執行緒上重新啟動，所以 TLS 陣列的位址不可以快取或最佳化為跨函式呼叫的通用子運算式 \(如需詳細資訊，請參閱 [\/Og \(全域最佳化\)](../../build/reference/og-global-optimizations.md) 選項\)。  **\/GT** 會阻止這種最佳化。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**啟用 Fiber\-safe 最佳化**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)